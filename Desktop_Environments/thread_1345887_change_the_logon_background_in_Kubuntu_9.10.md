---
title: "change the logon background in Kubuntu 9.10"
date: 2009-12-04
forum: Desktop Environments
---

### Post by optimistique1 on 2009-12-04
Hi All

Does anyone know how I change the logon background in Kubuntu 9.10 so that it is the same as the desktop background.

Many thanks

Garry

---

### Post by aysiu on 2009-12-05
I'm a bit rusty on KDE.

I think this may help, though. Paste these two commands into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo updatedb
locate kdmrc
``` Once you find the *kdmrc* file, edit it as root using ```
sudo -i
``` or ```
kdesu dolphin
``` and look for a line about the background and point that to the location of your background picture.

---

### Post by Zorael on 2009-12-08
Which background to display when the greeter (login screen) is shown is defined in the kdm theme. In 9.10, the default theme is **oxygen-air**, and it's located at **/usr/share/kde4/apps/kdm/themes/oxygen-air**. The actual background in use is the file there named **1280x800.jpg**.

You could copy that whole (theme) directory elsewhere, make the changes to the new directory as you please (change wallpaper), and then point kdm to use the new theme. You could either edit the **oxygen-air.xml** file and make it point at a different wallpaper at line **10**, or replace the **1280x800.jpg** file with your own.
```
	<item type="pixmap" id="background" background="true">
		<normal file="[COLOR="Green"]**1280x800.jpg**[/COLOR]" scalemode="crop"/>
		<pos width="100%" height="100%"/>
	</item>
```
To change which theme is to be used, there's a Login Manager section in System Settings, under the Advanced tab. Obviously it will require root privileges.

---

