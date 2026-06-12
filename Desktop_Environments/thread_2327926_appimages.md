---
title: "appimages"
date: 2016-06-15
forum: Desktop Environments
---

### Post by Johnny_D._Wicked on 2016-06-15
I'm having problems getting an appimage program like Krita 3.0 to run directly from the Unity Bar Launcher and Dash in Ubuntu 16.04 LTS 64-bit. I created the shortcut by opening up Krita first then right clicking on the icon in the unity bar launcher and chose add to dash and lock to launcher. But upon clicking on the created icon of the appimage, nothing happened; same results in both dash and launcher.

Clicking and opening the appimage file in my file manager directly and on desktop link works. BUT I want to have it working in the Unity bar launcher and dash. How do I fix this?

I've also tried Cairo-dock and docky but experienced same problems with appimage not opening directly from it.

---

### Post by vasa1 on 2016-06-15
Have you logged out and logged in again or rebooted after installing AppImage? Sometimes, that helps!

---

### Post by Johnny_D._Wicked on 2016-06-15
> **vasa1 said:**
> Have you logged out and logged in again or rebooted after installing AppImage? Sometimes, that helps!

Hey, Vsas1, I tried logging out and back in, even restart too but it still didn't work.

---

### Post by grahammechanical on 2016-06-16
I have been puzzled by your thread title. I think I finally understand what you are doing. You are installing the version of Krita that is packaged as an Appimage.  I was not familiar with this package format.

[https://krita.org/en/download/krita-desktop/](https://krita.org/en/download/krita-desktop/)

[http://appimage.org/](http://appimage.org/)

I recently installed the snap packaged version of Krita on Ubuntu 16.04. I do not have the problem that you are having. I hope that you resolve this issue.

Regards.

---

### Post by vasa1 on 2016-06-16
> **Johnny_D._Wicked said:**
> ...
Clicking and opening the appimage file in my file manager directly and on desktop link works. ...
Could you post the contents of the corresponding .desktop file? I understand that the AppImage installation process proposes creating a .desktop file for you.

BTW, you may want to read [Testing deb apps converted to snap apps on Ubuntu & flavours]("http://ubuntuforums.org/showthread.php?t=2327088") as an alternative which is what grahammechanical indicated.

---

### Post by Chanath on 2016-07-10
> **Johnny_D._Wicked said:**
> I'm having problems getting an appimage program like Krita 3.0 to run directly from the Unity Bar Launcher and Dash in Ubuntu 16.04 LTS 64-bit. I created the shortcut by opening up Krita first then right clicking on the icon in the unity bar launcher and chose add to dash and lock to launcher. But upon clicking on the created icon of the appimage, nothing happened; same results in both dash and launcher.

Clicking and opening the appimage file in my file manager directly and on desktop link works. BUT I want to have it working in the Unity bar launcher and dash. How do I fix this?

I've also tried Cairo-dock and docky but experienced same problems with appimage not opening directly from it.

Create a desktop file, for example, 
> [Desktop Entry]
Encoding=UTF-8
Name=Krita
Comment=whatever you like
Exec=~/Krita.....(the name you have) ( or /home/username/Krita...)
Type=Application
Icon=krita
Categories=Graphics;


Name is krita.desktop and put it in your /usr/share/applications
You see your Krita as an application in the unity bar.

Alternatively, you can make the krita.desktop file executable, and keep it in your file manager and create a link to the Unity Launcher. Then you don't have to put it in /usr/share/applications.

---

### Post by VanillaMozilla on 2016-07-16
Check the directory or file properties to see if it's executable.  If you haven't done so already, you have to make it executable, or in other words, give it permission to run.  From a Terminal:
chmod +x /pathtoAppImage
Or go to file properties, Permissions, and check the box.

---

