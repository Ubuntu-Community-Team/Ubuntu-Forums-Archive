---
title: "Is there a way to have screensaver start at login screen?"
date: 2011-01-26
forum: Desktop Environments
---

### Post by johncc on 2011-01-26
I'm running vanilla 10.04.  I have several users on the box, so it boots to the login screen (or whenever someone logs out).  Is there a way to set a screensaver to come on after the login screen has been idle for x minutes?  On my system the login screen just stays there "forever".

Thanks!
John

---

### Post by towheedm on 2011-01-26
The following works under Karmic (9.10) but should certainly work under Lucid (10.04) also.

Start by opening a terminal window.  Click on Applications > Accessories > Terminal.

Create a new *.desktop* file in the [COLOR=Blue]/usr/share/gdm/autostart/LoginWindow[/COLOR] directory by entering this command in the terminal:

```
gksudo gedit /usr/share/gdm/autostart/LoginWindow/gdm_screensaver.desktop
```Paste the following lines into gedit:

```
[Desktop Entry]

Type=Application
Name=Screensaver
Icon=/usr/share/icons/gnome/scalable/apps/screensaver.svg
Exec=gnome-screensaver

StartupNotify=true
Categories=GNOME;GTK;
X-Ubuntu-Gettext-Domain=gdm

```Save the file and close gedit.  Verify the file is saved by entering the following command in the terminal:

```
ls  /usr/share/gdm/autostart/LoginWindow
```You should see a file named gdm_screensaver.desktop among others.

The above procedure allows the screensaver to run at the login screen (the login screen is always run as a user called 'gdm').  Now to configure the screensaver for user gdm, enter this command in the terminal:

```
gksudo -u gdm dbus-launch gnome-screensaver-preferences
```Configure the screensaver as you would normally.

Please let me know if this works in 10.04.

If you would like to configure the login window even more, check out the link in this thread:

[http://ubuntuforums.org/showthread.php?t=1445724](http://ubuntuforums.org/showthread.php?t=1445724)

---

