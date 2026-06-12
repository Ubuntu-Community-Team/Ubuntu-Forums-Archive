---
title: "Kubuntu 15.04 Widget Appearance"
date: 2015-04-25
forum: Desktop Environments
---

### Post by gus_zernial on 2015-04-25
Installed Kubuntu 15.04. Minor question about desktop icon/shortcut/widget. Default icon background is translucent/grey. How do I change icon background to transparent/none?        Thx, Gus

---

### Post by Rog131 on 2015-04-25
1) Use a desktop theme with transparent background.

KDE System Settings > Workspace Theme > Desktop Theme

[img]http://i.imgur.com/zpyRdvA.png[/img]

2) Create/edit the theme:

- [https://techbase.kde.org/Development/Tutorials/Plasma5](https://techbase.kde.org/Development/Tutorials/Plasma5)
- [https://techbase.kde.org/Development/Tutorials/Plasma/Theme](https://techbase.kde.org/Development/Tutorials/Plasma/Theme)
- [https://techbase.kde.org/Development/Tutorials/Plasma5/ThemeDetails](https://techbase.kde.org/Development/Tutorials/Plasma5/ThemeDetails)

---

### Post by gus_zernial on 2015-04-25
I couldn't find TrustyAir to install, so I installed NoRa, which seems to be transparent (?). Then ls in ~/.local/share/plasma/desktoptheme/NoRa/widgets gives the below. Am I in the right directory? Which file do I edit?

actionbutton.svgz          button.svgz               identiconshapes.svgz  picker.svgz
action-overlays.svg        calendar.svgz             identicontheme.svgz   scrollbar.svgz
activities.svgz            checkmarks.svgz           krunner.svgz          scrollwidget.svgz
analog_meter.svgz          clock.svg                 labeltexture.svgz     slider.svgz
arrows.svgz                configuration-icons.svg   lineedit.svgz         systemtray.svg
background.svgz            containment-controls.svg  line.svgz             tasks.svgz
bar_meter_horizontal.svgz  dragger.svgz              listitem.svgz         timer.svgz
bar_meter_vertical.svgz    extender-background.svgz  luna.svgz             toolbar.svgz
battery-oxygen.svgz        extender-dragger.svgz     media-delegate.svgz   toolbox.svgz
branding.svgz              eyes.svg                  notes.svg             tooltip.svgz
busywidget.svgz            frame.svgz                pager.svgz            translucentbackground.svgz
button4.svgz               glowbar.svgz              panel-background.svg  viewitem.svgz

---

### Post by Rog131 on 2015-04-26
Earlier should be :

> 1) Use a desktop theme with transparent background.
2) Or create/edit the theme:




Plasma themes & parts are described: [https://techbase.kde.org/Development/Tutorials/Plasma5/ThemeDetails](https://techbase.kde.org/Development/Tutorials/Plasma5/ThemeDetails)


Editing a theme - Using the Breeze theme as example.

Copying the Breeze from /usr/share/plasma/desktoptheme/default/ to ~/.local/share/plasma/desktoptheme/MyBreeze/.

[img]http://i.imgur.com/rJkdb5n.png[/img]

Editing the metadata.desktop

Changes:
Name=MyBreeze
Name[x-test]=xxMyBreezexx


Editing the widget background -  [https://techbase.kde.org/Development/Tutorials/Plasma5/ThemeDetails](https://techbase.kde.org/Development/Tutorials/Plasma5/ThemeDetails)

> Current Theme Elements

...Each theme is stored in a subdirectory with the following file structure

/widgets: generic desktop widget background...

/background.svg: a background image for plasmoids....

Opening the /widgets/background.svgz file in a svg editor (Inkscape)

[img]http://i.imgur.com/tsWOnn1.png[/img]

Editing only the middle - this is only an example.

Saving.

Cleaning the cache: ~/.cache/...  Removing the plasma-svgelements and the kcache files.

Changing the desktop theme to the MyBreeze.

The Widget background is transparent.

[img]http://i.imgur.com/fNdgJnX.png[/img]

---

