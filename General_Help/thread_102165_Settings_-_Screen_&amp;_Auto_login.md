---
title: "Settings - Screen &amp; Auto login"
date: 2005-12-11
forum: General Help
---

### Post by janboen on 2005-12-11
Hi there,

My Ubunutu box is being used as a home hosted web server.
It's running without monitor, keyboard and mouse.

I've got two things that I want to get done:
1- Get the system to boot without monitor attached with a screen resolutions 1024x768 or 1280x1024.
.  Today it starts with 640x480 without a monitor
2- Once booted it should automaticaly login to the GNOME so I can remotely manage my system with VNC.
.  Today it stops at the login screen and I need to enter user name and password.

Thanks up front for your help.

Jan

Use YACS ([http://www.yetanothercommunitysystem.com/](http://www.yetanothercommunitysystem.com/)) as web front end or blogging tool. It's great and it's free!!!

---

### Post by Zelut on 2005-12-11
If you're running it as a web server I wonder why you have the Desktop GUI installed at all.  I'm also running a small [web server]("http://www.howtoforge.com/perfect_setup_ubuntu_5.10") but I used the 'server'.  have you tried that or is there a specific reason that you still need the GUI despite not having a monitor attached?

Ohh, I do all of my remote maintenance thru ssh on the terminal.

---

### Post by matid on 2005-12-11
2. System -> Administration -> Login Screen Setup -> General -> Automatic Login:
Check 'Login a user automatically on first bootup' and then choose the user from 'Automatic login username' dropdown list.

BTW: it should be much easier to enable XDMCP than to use VNC. If you use XDMCP you don't have to control already logged in user, you can simply use X to log in. Try this:
System -> Administration -> Login Screen Setup -> Security -> Enable XDMCP

---

### Post by janboen on 2005-12-12
Which client would I need to install on my windows PC to use XDMCP?

---

### Post by janboen on 2005-12-12
I use the gui to do some local maintenance jobs.
I've lost the habit of doing things from the CLI.

---

