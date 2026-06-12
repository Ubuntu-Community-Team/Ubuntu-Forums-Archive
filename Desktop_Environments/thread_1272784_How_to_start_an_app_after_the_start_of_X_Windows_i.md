---
title: "How to start an app after the start of X Windows in Gnome"
date: 2009-09-22
forum: Desktop Environments
---

### Post by floatingworld on 2009-09-22
I have a fair bit of experience with Linux on the server via bash but I'm new to Linux on the desktop.

I have installed and I'm currently using qjoypad, which translates a joystick's input into mouse movements.  But every time I reboot my system, log in through the gdm, and X starts, I have to separately press Alt-F2 to get the run dialog and start qjoypad from there.

So I'm just looking to find out what the standard way is to start an app automatically after X finishes starting; I'd imagine that there's something like the rc scripts for when Linux switches runlevels.  Preferably I'd like to know what the standard is for Ubuntu in particular, but if there's a convention for Gnome or for X itself that's good too.  I don't need an in-depth description, just a link or the keywords to search for would help.

Thanks in advance, fw

---

### Post by doas777 on 2009-09-22
well,
the items listed in System -> Preferences -> Startup applications
all fire after a login. is that too late in the process for your needs?

---

### Post by floatingworld on 2009-09-23
Not too late at all - thanks, doas777, that's exactly what I need!  I simply hadn't noticed that.

I wish there was some way on this forum to mark the comments of people who give a good answer.

---

