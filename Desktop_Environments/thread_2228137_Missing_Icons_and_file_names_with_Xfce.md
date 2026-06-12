---
title: "Missing Icons and file names with Xfce"
date: 2014-06-05
forum: Desktop Environments
---

### Post by gga96 on 2014-06-05
Hi all,

Setting up Xfce as my desktop and have 2 small issues:
1:- With Thurnar(1.6.3) does not show icons. The Preferences and View>"View as Detailed List" have been set.
2:- With gedit(3.10.4) the file name tab bar is blank with not file names showing.

Does anyone know how to correct this?
Glen

---

### Post by Toz on 2014-06-05
What appearance theme and icon theme are you using? (look in Settings Manager >> Appearance). Have you tried changing them to see if it helps? For the gedit issue, you should try with a GTK3 theme like Greybird or Bluebird).

---

### Post by gga96 on 2014-06-06
Thanks Toz.
I tried your suggestions but no success.
I seems icons are not found by Thunar.
The gedit problem seems more like a bug.

---

### Post by Toz on 2014-06-06
Can we see the results of:
```
ps -ef | grep xf
```
...as well as:
```
xfconf-query -c xsettings -lv
```

---

### Post by monkeybrain20122 on 2014-06-06
Is this xubuntu or xfce4 on some *buntu (other than xubuntu)?

I have exprienced this and it is very odd:
1) Have icons in new Xubuntu install (14.04)
2) No icons if I install xfce4 on Ubuntu and switch to it.
3) No icons if I do a fresh isntall of Xubuntu 14.04 with an already present /home partition of xubuntu 12.04

Unfortunately I have no solution and haven't persuited it as xfce is not my DE.

---

### Post by gga96 on 2014-06-06
Thanks Toz the requested data follows:
```

glen@hp-dev:~$ ps -ef | grep xf
glen      1205  1087  0 07:16 ?        00:00:00 /bin/sh /etc/xdg/xfce4/xinitrc -- /etc/X11/xinit/xserverrc
glen      1234  1205  0 07:16 ?        00:00:00 xfce4-session
glen      1275  1087  0 07:16 ?        00:00:00 /usr/lib/x86_64-linux-gnu/xfce4/xfconf/xfconfd
glen      1280  1234  0 07:16 ?        00:00:00 xfwm4 --display :0.0 --sm-client-id 2bc898c03-588e-46e0-be3e-1a0b55deefe5
glen      1297  1234  0 07:16 ?        00:00:00 xfce4-panel --display :0.0 --sm-client-id 2a188b3c8-276c-4187-96ea-849b39b4713b
glen      1312  1234  0 07:16 ?        00:00:00 xfdesktop --display :0.0 --sm-client-id 211c417c0-cec3-4d68-aed0-3b4d28817ca6
glen      1313  1087  0 07:16 ?        00:00:00 xfsettingsd --display :0.0 --sm-client-id 279cc2aea-7a4d-4383-bdb0-c1c8270ca239
glen      1321  1297  0 07:16 ?        00:00:00 /usr/lib/x86_64-linux-gnu/xfce4/panel/wrapper-1.0 /usr/lib/x86_64-linux-gnu/xfce4/panel/plugins/libsystray.so 6 18874400 systray Notification Area Area where notification icons appear 
glen      1323  1297  0 07:16 ?        00:00:00 /usr/lib/x86_64-linux-gnu/xfce4/panel/wrapper-1.0 /usr/lib/x86_64-linux-gnu/xfce4/panel/plugins/libactions.so 2 18874401 actions Action Buttons Log out, lock or other system actions 
glen      1329  1234  0 07:16 ?        00:00:00 xfce4-terminal --geometry=147x24 --display :0.0 --role=xfce4-terminal-1401833163-657437704 --show-menubar --show-borders --hide-toolbar --working-directory 
/home/glen --sm-client-id 289bc0e7e-6727-49c0-8abd-08a6dc35a7be
glen      1428  1087  0 07:16 ?        00:00:00 xfce4-volumed
glen      2043  1604  0 07:29 pts/1    00:00:00 grep --color=auto xf

glen@hp-dev:~$ xfconf-query -c xsettings -lv
/Gtk/ButtonImages               true
/Gtk/CanChangeAccels            false
/Gtk/ColorPalette               black:white:gray50:red:purple:blue:light blue:green:yellow:orange:lavender:brown:goldenrod4:dodger blue:pink:light green:gray10:gray30:gray75:gray90
/Gtk/CursorThemeName            
/Gtk/CursorThemeSize            0
/Gtk/FontName                   Sans 10
/Gtk/IconSizes                  
/Gtk/KeyThemeName               
/Gtk/MenuBarAccel               F10
/Gtk/MenuImages                 true
/Gtk/ToolbarIconSize            3
/Gtk/ToolbarStyle               icons
/Net/CursorBlink                true
/Net/CursorBlinkTime            1200
/Net/DndDragThreshold           8
/Net/DoubleClickDistance        5
/Net/DoubleClickTime            400
/Net/EnableEventSounds          false
/Net/EnableInputFeedbackSounds  false
/Net/IconThemeName              elementary-xfce-dark
/Net/SoundThemeName             default
/Net/ThemeName                  Xfce-4.0
/Xft/Antialias                  -1
/Xft/Hinting                    -1
/Xft/HintStyle                  hintnone
/Xft/RGBA                       none

```

Thanks monkeybrain20122 I am new to ubuntu and Xfce4 but your experience sounds like it echos mine.
I installed ubuntu 14.04 and then installed and switched to Xfce4.

---

### Post by Toz on 2014-06-06
Try installing the gnome-icon-theme-full and tango-icon-theme packages:
```
sudo apt-get install gnome-icon-theme-full tango-icon-theme
```
...log out and back in again, then change the icon theme in Settings Manager >> Appearance >> Icons.

---

### Post by gga96 on 2014-06-07
You have cracked it Toz the icons are now alive. Thanks.

That leaves gedit . I could not discover a method that would apply your original suggestion:
> 
For the gedit issue, you should try with a GTK3 theme like Greybird or Bluebird).

---

### Post by Toz on 2014-06-07
Can you upload a screenshot of it?

According to your previous post, you are using the Xfce-4.0 Appearance theme. Can you change it to Greybird or Bluebird and see if it helps. If you don't have those themes installed, try installing the shimmer themes package:
```
sudo apt-get install shimmer-themes
```
I'm thinking it might be a GTK3 issue and you need to use an appearance theme that supports GTK3. Xfce-4.0 does not.

After you've done so, can you post back again:
```
xfconf-query -c xsettings -lv
```

NOTE: To change the appearance theme, go to Settings Manager >> Appearance.

---

### Post by gga96 on 2014-06-10
Hi Toz,  gedit now has file names, thanks.

None of the Xfce styles or Raleigh work, the gedit page tab tile space is black, the other style produce a readable file name. I am now using Bluebird
I enclose the following for you debug info. The shimmer themes did not show up in Appearance>Styles.
```

glen@hp-dev:~$ sudo apt-get install shimmer-themes
[sudo] password for glen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
shimmer-themes is already the newest version.
0 to upgrade, 0 to newly install, 0 to remove and 12 not to upgrade.

glen@hp-dev:~$ xfconf-query -c xsettings -lv
/Gtk/ButtonImages               true
/Gtk/CanChangeAccels            false
/Gtk/ColorPalette               black:white:gray50:red:purple:blue:light blue:green:yellow:orange:lavender:brown:goldenrod4:dodger blue:pink:light green:gray10:gray30:gray75:gray90
/Gtk/CursorThemeName            
/Gtk/CursorThemeSize            0
/Gtk/FontName                   Sans 10
/Gtk/IconSizes                  
/Gtk/KeyThemeName               
/Gtk/MenuBarAccel               F10
/Gtk/MenuImages                 true
/Gtk/ToolbarIconSize            3
/Gtk/ToolbarStyle               icons
/Net/CursorBlink                true
/Net/CursorBlinkTime            1200
/Net/DndDragThreshold           8
/Net/DoubleClickDistance        5
/Net/DoubleClickTime            400
/Net/EnableEventSounds          false
/Net/EnableInputFeedbackSounds  false
/Net/IconThemeName              Tango
/Net/SoundThemeName             default
/Net/ThemeName                  Bluebird
/Xft/Antialias                  -1
/Xft/Hinting                    -1
/Xft/HintStyle                  hintnone
/Xft/RGBA                       none

```

---

### Post by Toz on 2014-06-10
Glad to hear you got it working
> **gga96 said:**
> The shimmer themes did not show up in Appearance>Styles.
Shimmer themes is a collection of themes, of which Bluebird is one. Greybird, Alatross and Blackbird being the others. These themes support both the GTK2 and GTK3 toolkits. gedit is written using the GTK3 toolkit and requires a theme that supports GTK3.

---

### Post by quang777 on 2015-05-18
I know this is a little old thread, but it seems pertinent. Does anyone know how to make certain defaults "global" for all users on a system?
Example, if I want to make the Greybird the default theme for all users on machineX, is there a file that is sourced globally? I'd like to make a global default for both the Theme and the Icon pack.

---

