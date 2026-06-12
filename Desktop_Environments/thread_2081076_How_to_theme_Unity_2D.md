---
title: "How to theme Unity 2D"
date: 2012-11-05
forum: Desktop Environments
---

### Post by vanlong441 on 2012-11-05
Below are important values and their locations you can change to theme Unity-2D launcher, dash and their components. Here is the result from [_LPinguy_]("https://sourceforge.net/projects/lpinguy/")

[https://sourceforge.net/projects/lpinguy/screenshots/Workspace%201_005.png](https://sourceforge.net/projects/lpinguy/screenshots/Workspace%201_005.png)

[https://sourceforge.net/projects/lpinguy/screenshots/Workspace%201_002.png](https://sourceforge.net/projects/lpinguy/screenshots/Workspace%201_002.png)

[COLOR=Red]Notice that after an upgrade of Unity-2D all will go  back to their default settings. Therefore, remember to make a backup everytime  you've done something![/COLOR]

[COLOR="DarkGreen"]/usr/share/unity-2d[/COLOR]

> **/launcher/Launcher.qml**

    Rectangle {
        Accessible.name: "background"
        color: "#DEDEDE"
        opacity: 1.00

            id: border
                 width: 0

    Component.onCompleted: {
        items.appendModel(bfbModel);
        items.appendModel(applications);
        items.appendModel(devices);
        shelfItems.appendModel(trashes);

**/common/IconTile.qml**

        sourceSize.width: 48
        sourceSize.height: 48

**/common/TextCustom.qml**

    Text {
        color: "#000000"

**/dash/Dash.qml**

            id: panelBorder

            id: search_entry
                height: 42

            id: filterPane
                 width: 300
         anchors.rightMargin: 15

            id: lensBar
               height: 44

**/dash/LensBar.qml**

        id: background
                 color: "black"
                 opacity: 0

[B]/dash/TileHorizontal.qml
/dash/TileVertical.qml[/B]
            color: "#000000"

**/dash/FilterPane.qml**
        effect: DropShadow {
                    color: "black"
**/common/Background.qml**

        effect: ColorizeEffect {
            color: unity2dConfiguration.averageBgColor
            saturation: 0.0

            id: blurredBackground
                effect: Blur {blurRadius: 0}

            source: "artwork/background_sheen.png"
            opacity: 1.0

        property int bottomThickness: 38
        property int rightThickness: 37

---

