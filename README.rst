QML Icons
=========

Use Material icon font (or other icon fonts like FontAwesome, fontello...) in QML.

.. image:: example/screenshot.png
    :alt: Screenshot

Usage
-----

To use the icons in your project, follow these steps:

- Add the font to the application font database.

.. code:: cpp

    if (QFontDatabase::addApplicationFont(":/icons/MaterialIcons-Regular.ttf") == -1)
        qWarning() << "Failed to load font Material";

- Add the image provider to the application engine.
   
  Here you need to specify the image provider name and, in the
  IconProvider constructor, you must give the font family name and
  the json file that contains the conversion keys from the icons name
  to the characters code.

.. code:: cpp

    #include "iconprovider.h"

    ...

    QQmlApplicationEngine engine;
    engine.addImageProvider("icon",
                            new IconProvider("Material Icons", ":/icons/codepoints.json"));

- Use the icons in any QML item that requires an image.

.. code:: qml

    ToolButton {
        icon.source: "image://icon/info"
        icon.color: Material.foreground
    }

    ItemDelegate {
        icon.source: "image://icon/settings"
        text: "Settings"
    }
