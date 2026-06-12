---
title: "Disabling Desktop Startup"
date: 2009-02-01
forum: Desktop Environments
---

### Post by dividenot on 2009-02-01
I'm wondering how to make it so Gnome doesn't startup when i start the computer.  

What I want is to have the command prompt only on start up and be able to call the desktop only when needed.

I'm running the server edition of Ubuntu and I'm really only using the desktop to become familiar with Ubuntu.  Ideally I would only need to use the command prompt.

I know about the /etc/init.d/gdm stop/start/restart commands.  But I'd like to find some kind of file or setting I can change to make it so either gdm, the x server, or gnome doesn't start up with the computer.

I've been using Ubuntu, and Linux, for only a few months now and I'm not sure of the best way to go about this.

---

### Post by yoyoned on 2009-02-01
gdm is the login manager that is automatically started.  On servers, I like to just uninstall gdm.

If required, you can get back to gnome by logging in the the terminal and typing startx

---

### Post by yoyoned on 2009-02-01
or instead of removing gdm, you could just stop it from starting up.  

[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)

---

