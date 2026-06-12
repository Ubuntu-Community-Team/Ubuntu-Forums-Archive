---
title: "GnomeBaker not showing up on Panel"
date: 2005-07-10
forum: Desktop Environments
---

### Post by filemanager on 2005-07-10
I installed GnomeBaker, but it isn't showing up on the menu.

I ran killall gnome-panel but it still isn't showing up.

I reinstalled it via Synaptic, but still not on the menu.

Does this mean it's not installed properly or what?

---

### Post by mtron on 2005-07-10
first check if the installation went ok, by typeing "gnomebaker" in a terminal window. this will launch the app.

Then istall a menu editor: [http://www.ubuntuguide.org/#menu-editor](http://www.ubuntuguide.org/#menu-editor)

in the menu editor, go to "Accessoirs" & create a new launcher with the following properties:
Name:GnomeBaker CD/DVD Creator
Command: gnomebaker
Icon: /usr/share/gnomebaker/gnomebaker-48.png

cheers mtron

---

### Post by filemanager on 2005-07-10
[QUOTE=mtron]first check if the installation went ok, by typeing "gnomebaker" in a terminal window. this will launch the app.

Then istall a menu editor: [http://www.ubuntuguide.org/#menu-editor](http://www.ubuntuguide.org/#menu-editor)

in the menu editor, go to "Accessoirs" & create a new launcher with the following properties:
Name:GnomeBaker CD/DVD Creator
Command: gnomebaker
Icon: /usr/share/gnomebaker/gnomebaker-48.png

cheers mtron[/QUOTE]
 Cool, thanks!!

How come it goes in Accessories and not in Sound/Video? Just curious, as I think the menu goes into Accessories by default anyway

---

### Post by darkmatter on 2005-07-10
[QUOTE=filemanager]How come it goes in Accessories and not in Sound/Video? Just curious, as I think the menu goes into Accessories by default anyway[/QUOTE]

The reason would be that it is not an application strictly limited Sound/Video, as it is also meant to handle data/.iso's. Like any decent burning utility, it's a jack-of-all-trades.

---

