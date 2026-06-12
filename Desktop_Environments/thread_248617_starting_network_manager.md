---
title: "starting network manager"
date: 2006-09-01
forum: Desktop Environments
---

### Post by Hårek on 2006-09-01
I've just installed network manager thru SPM. I need it to be able to access wlan on campus. [http://www.sai.uio.no/it/oppkobling/wireless-linux-eng.html](http://www.sai.uio.no/it/oppkobling/wireless-linux-eng.html) 

But how do you start the program? It doesn't list under applications->internet or any other place. I try to add the program thru the ADD/remove application option, but according to it its allready listed in Applications->internet

I've removed wifi-radar thru SPM, and disabled it in network settings. 

please help! I'm out of ideas

---

### Post by ciscosurfer on 2006-09-01
Add the following to System > Preferences > Sessions | Startup Programs | Add```
nm-applet --sm-disable
```Click 'OK', then 'Close'.  Then, in a terminal, issue the following and hit Enter```
sudo gtk-update-icon-cache -f /usr/share/icons/hicolor
```Now, logout and then log back in.  Your network manager applet will appear in the upper-right corner. :D

---

### Post by Varjagy on 2006-11-16
Well, I have the same problem as Hårek, but I don't want an Icon in the upper right corner, I want it under Applications-Internet. It said it would be there, but it's not. How can I fix that?

---

### Post by ciscosurfer on 2006-11-16
You need to create what's called a .desktop file, here's how to do that:[LIST=1]
[*]Open a terminal, Applications > Accessories > Terminal
[*]Go to **/usr/share/applications** by entering in the following and then pressing Enter```
cd /usr/share/applications
```
[*]Now we'll make the file and enter it to add the code necessary to allow it to show up in the Internet submenu of Applications```
sudo gedit nm-applet.desktop
```
[*]Your new file will open in gedit and you'll add the following (this is what mine looks like:[/LIST][INDENT][INDENT][Desktop Entry]
Encoding=UTF-8
Name=Network Manager
Comment=Network Manager applet
Icon=nm-device-wireless
Exec=nm-applet --sm-disable
Terminal=false
Type=Application
Categories=Application;Network;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=NetworkManager
X-GNOME-Bugzilla-Component=general
X-GNOME-Autostart-enabled=true
X-AppInstall-Package=network-manager-gnome
X-AppInstall-Section=main
[/INDENT][/INDENT]Save the file, logout, and then log back in.  If the icon doesn't show up, then you should try creating the file here instead: 

** /usr/share/app-install/desktop/nm-applet.desktop**

So that would be```
sudo gedit /usr/share/app-install/desktop/nm-applet.desktop
```

---

