---
title: "Deleted Items icon doesn't change whether empty or full"
date: 2008-08-10
forum: Desktop Environments
---

### Post by stormtrooprdave on 2008-08-10
I was trying out different icons for my wastebasket and now its stuck with one icon whether the bin is empty or full, it doesnt change the icon to show if there are files in the bin or not.

I was changing it by right clicking properties and clicking on the icon.  How can I get it to restore the 'pair' of icons that show if its empty or full?

---

### Post by silkstone on 2008-08-10
Try changing the Theme and then change it back again.

or...

Remove the Trash icon from the panel, and then right-click, Add to Panel and put it back.

or...

sudo apt-get install --reinstall gnome-applets

---

### Post by stormtrooprdave on 2008-08-10
I don't want to change the theme as I spent a long time customizing individual folder icons and suchlike.  I tried using gTweakUI to remove the trash from the desktop and putting it back but it stayed the same.  Its showing a full bin icon even though its empty

---

### Post by silkstone on 2008-08-10
OK, try this...

Applications > System tools > Configuration editor > apps > panel > applets > trashapplet_screen0

Check the box marked 'use_custom_icon'. If it is already checked, uncheck it.

---

### Post by stormtrooprdave on 2008-08-10
> **silkstone said:**
> OK, try this...

Applications > System tools > Configuration editor > apps > panel > applets > trashapplet_screen0

Check the box marked 'use_custom_icon'. If it is already checked, uncheck it.
It wasnt there.  I'm not sure we're talking about the same trashbin.  I'm talking about the one on the desktop, I don't have one on the panels at the top and bottom of the screen.
Do I need to do something in nautilus?

---

### Post by stormtrooprdave on 2008-08-11
I changed the theme and changed it back again but it didnt solve the problem.  

I think because I changed the deleted items icon manually it doesnt change when changing the whole theme.

---

### Post by silkstone on 2008-08-11
There isn't a Trash icon on the desktop by default - only on the bottom panel - so you must have added that.

You get to it by...

Applications > System tools > Configuration editor > apps > nautilus > desktop

That has a box for displaying a desktop Trash icon.

Have you tried...

sudo apt-get install --reinstall gnome-applets ?

---

### Post by stormtrooprdave on 2008-08-11
> **silkstone said:**
> There isn't a Trash icon on the desktop by default - only on the bottom panel - so you must have added that.

You get to it by...

Applications > System tools > Configuration editor > apps > nautilus > desktop

That has a box for displaying a desktop Trash icon.

Have you tried...

sudo apt-get install --reinstall gnome-applets ?
Just tried it but it didnt work.  I found this on another forum and wonder is there something like this I can do where I can specify what icon the bin will have when its full or empty?  If I right click and change it through properties thats when it stays the same whether its full or not, so I think I need something like this:

The way I got it in Kubuntu (and I think it should work with any window manager/DE with slight modification) is to create a new file ~/Desktop/Trash.desktop. The contents of the file are:

[Desktop Entry]
Comment=Contains removed files
EmptyIcon=trashcan_empty
Encoding=UTF-8
Icon=trashcan_full
Name=Trash
Name[en_US]=Trash
Type=Link
URL=trash:/

---

### Post by stormtrooprdave on 2008-08-11
I found this in /home/dave/.nautilus/metafiles/x-nautilus-desktop:%2F%2F%2F.xml.  I've highlighted the relevant bit.

<?xml version="1.0"?>
<directory><file [COLOR="Black"]name="XP.volume" timestamp="1218367438" icon_position="64,102" custom_icon="file:///home/dave/.icons/Mac_OS_X_Leopard_for_Debian_v1.4/scalable/devices/gnome-dev-harddisk.png"/><file name="computer" timestamp="1216750266" icon_position="64,102"/>[COLOR="Red"]<file name="trash" timestamp="1218460118" icon_position="64,22" custom_icon="file:///home/dave/.icons/Mac_OS_X_Leopard_for_Debian_v1.4/scalable/places/user-trash-full.png"/>[/COLOR]<file name="Ubuntu%208.04%20amd64.volume" timestamp="1215636678" icon_position="64,122"/><file name="Blank%20CD-R%20Disc.volume" timestamp="1216646806" icon_position="64,322"/><file name="Audio%20Disc.volume" timestamp="1216647272" icon_position="64,322"/><file name="home" timestamp="1216750264" icon_position="64,202"/><file name="2.1%20GB%20Media.volume" timestamp="1216761450" icon_position="64,122" custom_icon="file:///home/dave/.icons/LiNsta-0.3/scalable/devices/gnome-dev-usbdrive.png"/><file name="2.1%20GB%20Media.volume.2" timestamp="1216761328" icon_position="220,122"/><file name="2.0%20GB%20Media.volume" timestamp="1216800565" icon_position="64,122"/><file name="32.8%20GB%20Media.volume" timestamp="1216831840" icon_position="64,122"/><file name="BF2%20DVD.volume" timestamp="1218288225" icon_position="64,202"/></directory>

It shows the layout for my desktop but the information for the trash icon only lists one icon,  is there anywhere like this that stores the icon pathway for the full and empty icons?[/COLOR] Then I can just go and edit the pathway

---

### Post by stormtrooprdave on 2008-08-14
Bump!

Still haven't sorted this.  Any ideas anyone?

---

### Post by mewho on 2009-01-27
I have the exact same problem...I was wondering if anyone has any ideas.  thanks

---

