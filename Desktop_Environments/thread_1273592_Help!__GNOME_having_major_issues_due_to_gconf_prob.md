---
title: "Help!  GNOME having major issues due to gconf problem"
date: 2009-09-23
forum: Desktop Environments
---

### Post by Doughy on 2009-09-23
Today I booted my computer to find that Gnome is not loading correctly.  The login screen comes up perfectly, but when Gnome starts to load, I get multiple errors in ugly old-school looking gnome icons that says:

> An error occurred while loading or saving configuration information for evolution-alarm-notify.  Some of your configuration settings may not work properly.

Then, I just have a blank screen that has the default gnome background color, but no wallpaper.  Applications run if I launch them with gnome-do, but they don't have close/minimize buttons.  The terminal will not load unless I move to a different TTY.  In my /var/log/messages, I have this error:

> /var/log/daemon.log:Sep 23 09:37:14 geek-school x-session-manager[3418]: WARNING: Error retrieving configuration key '/desktop/gnome/session/idle_delay': Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Could not send message to gconf daemon: Message did not receive a reply (timeout by message bus)) 

Any help please?!!

EDIT:  I haven't changed much on my computer, but did install some packages yesterday that may have caused the problem.  I installed the music-applet and exaile music player from their PPA.  I also updated some other stuff yesterday, but can't remember what the packages were exactly.

---

### Post by Giblet5 on 2009-09-24
A "safe" (brute force) way to recover from "experiments" is to execute the following commands from the console (Ctrl-Alt-F1).

Login as yourself:
```
cd ..
sudo /etc/init.d/gdm stop
sudo mv $HOME $HOME.backup
sudo mkdir $HOME
sudo chown $LOGNAME:$LOGNAME $HOME
sudo chmod 755 $HOME
sudo /etc/init.d/gdm start
```

You'll be able to login with the Ubuntu defaults settings, and **all of your documents, pictures, etc, are in ../yourname.backup** where you can selectively copy them to your new home.

Note that NOTHING will be configured (IM, email, etc). You may want to copy (from ../yourname.backup) the .evolution folder, .purple, .mozilla, etc to recover IM and email data, but avoid .gconf*, .gtk*, .kde*, and .gnome*.

---

### Post by Doughy on 2009-09-25
OK, the problem has been solved.  My hard drive was going bad and was having read errors.  It just so happened that the corrupted portions of the HD were affecting gconf.  When I tried reinstalling Ubuntu, the installation failed and told me the drive was having errors, even though fsck didn't find them.

I replaced the HD and Ubuntu installed correctly.

---

