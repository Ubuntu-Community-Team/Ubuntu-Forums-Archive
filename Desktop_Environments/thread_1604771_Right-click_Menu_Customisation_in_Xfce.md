---
title: "Right-click Menu Customisation in Xfce?"
date: 2010-10-24
forum: Desktop Environments
---

### Post by Yukon-Jack on 2010-10-24
Howdy,

I'm trying to figure out how I can customise the menus  that appear when I right-click on one of my panels or the desktop in  Xfce 4.6.2 under Xubuntu 10.10.  I was able to use Gnome  menu editor to get the standard
menus up to snuff but it will do nothing for the right-click menus.

I have no aversion to manually editing config files if that's what it takes, I just cant seem to find the right ones.
Any help would be appreciated.

   - Jack of the Yukon

---

### Post by ankspo71 on 2010-10-24
Hi,
I don't use XFCE now, but when I did, I remember it not having a menu editor. It was a turn off for me because every attempt to manually add a menu item didn't work for me.

Anyways, here is a few links and ideas that may help:
1. Create application launchers in the right click menu of the desktop:
[http://xfcemenuedit.mon-asso.org/index.en.html](http://xfcemenuedit.mon-asso.org/index.en.html)
This handles the editing of "xfdesktop root menu" which is described near the bottom of the page here:
[http://www.xfce.org/documentation/4.0/manuals/xfdesktop](http://www.xfce.org/documentation/4.0/manuals/xfdesktop)

2. Manually edit the menus:
[http://xubuntu.wordpress.com/2006/07/12/manually-edit-the-xfce-menu/](http://xubuntu.wordpress.com/2006/07/12/manually-edit-the-xfce-menu/)

Other options:
1. Use the **xfapplet panel plugin** (an XFCE applet that allows using gnome applets) this way you can use the Gnome menu in XFCE. Here is the tip for this: [http://wiki.xfce.org/tips](http://wiki.xfce.org/tips) Homepage: [http://goodies.xfce.org/projects/panel-plugins/xfce4-xfapplet-plugin](http://goodies.xfce.org/projects/panel-plugins/xfce4-xfapplet-plugin) Edit: this applet is available in Ubuntu's repositories.

2. Create desktop shortcuts to launch applications. 

3. Consider using a dock or other application launcher - one that allows creating your own application shortcuts. XFCE does have its own 2D(3D?) desktop effects (transparency with shadows - compositing) so it is capable of running 'most' docks by default, providing you enable this feature. Edit: To enable this compositing, go to Menu > Settings > XFE4 Settings Manager > Window Manager Tweaks > Compositor then enable "Enable Display Compositing".

I hope at least one of these ideas help.

---

### Post by Yukon-Jack on 2010-10-24
Much appreciated ankspo71.
I want to remove all options from the panels context menu and from the desktop's context menu I want the "create new *" and "open terminal here" options.  I'll try out your suggestions.

---

