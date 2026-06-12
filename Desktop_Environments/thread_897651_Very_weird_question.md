---
title: "Very weird question?"
date: 2008-08-22
forum: Desktop Environments
---

### Post by gabo.cr on 2008-08-22
I have Ubuntu.
You can call me crazy, but I would like to know if I can reboot the computer loading only one program on the screen without showing the desktop.
I want to find a way to start the computer where you can only see an specific program and not be able to see the desktop or any other programs.
But I also want to be able to get on the desktop in case I need to fix something, using some kind of a root access.
Any ideas?  :confused:

---

### Post by tuxxy on 2008-08-22
You need to startx for any GUI app, which will start the DE you use.

---

### Post by ByteJuggler on 2008-08-22
> **gabo.cr said:**
> I have Ubuntu.
You can call me crazy, but I would like to know if I can reboot the computer loading only one program on the screen without showing the desktop.
I want to find a way to start the computer where you can only see an specific program and not be able to see the desktop or any other programs.
But I also want to be able to get on the desktop in case I need to fix something, using some kind of a root access.
Any ideas?  :confused:

It should be possible to set up a user with a .xsession or .XStartup (sorry I forget the details off the top of my head) script to replace the default window manager and instead simply directly run a single application on top of the X window system.  Doing this will also mean no window manager frills but it sounds like that's what you actually want.  I'll try to post exact instructions when I get home tonight.

---

### Post by damis648 on 2008-08-22
Create a separate account for this purpose, an unprivileged user, and a separate "admin" account (separate from this non-desktop account and separate from root, with administrator privileges). Start by pressing Alt+F2 and type gconf-editor and enter. In the program that opens, navigate to: Apps>Metacity>General. If you would like to remove the close, minimize, and maximize buttons, (most likely you will I would guess), clear the field "button_layout". All buttons will disappear. Now close that with Alt+F4. Now go to System>Preferences>Sessions and add the application you would like to start, command being the name (pidgin, firefox, whatever). Now close that, Alt+F4. Now delete the bottom panel. Create a new panel by right clicking the top panel and drag it somewhere. Put a single applet in there, the shutdown applet, by right clicking on the panel. Now delete the top panel. That should do it. Just move you shutdown panel where you want. You might want to add a launcher to your app on the desktop, in case someone manager to close it. Now press Ctrl+Alt+Backspace and log into your "Admin" account. Now go to System>Administration>Login Window and set your special non-desktop account to login automatically. To administer the system, all you have to do id "Log Out" from the shutdown menu in your special account. Good Luck!

---

### Post by gabo.cr on 2008-08-22
ByteJuggler, that's exactly what I want to do.
I red about "startx" and also about the "Init scripts" in Ubuntu documents.
It is very interesting, but not really related on what I'm trying to do.
The beauty of Open Source is that one could possibly do it !!!
:)

---

### Post by gabo.cr on 2008-08-22
damis648, that sounds fun !!, I will try that too.
:)

---

### Post by maniheer on 2008-08-22
This is what I would do if I wanted to start xterm on its own.

```

sudo gedit /usr/share/xsessions/XtermSession.Desktop

```

```

[Desktop Entry]
Encoding=UTF-8
Name=Xterm
Comment=
Exec=xterm
Icon=
Type=Application

```

and save it.

Then log out and it should be there as an option in GDM (or whatever)

It should be anyway :)

---

