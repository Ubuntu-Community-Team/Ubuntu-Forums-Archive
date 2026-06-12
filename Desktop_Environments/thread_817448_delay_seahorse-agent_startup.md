---
title: "delay seahorse-agent startup"
date: 2008-06-03
forum: Desktop Environments
---

### Post by Charlotte18 on 2008-06-03
In the logon process for individual users, is there any way to make the seahorse-agent start up later? I ask this because it seems that when AD users logon to my Hardy desktops that are joined to the domain, these users are getting kicked off right away because of "could not get password information for UID of current process" and "failed due to unknown user id" errors. The users logon okay, but the desktop gives a "your session only lasted 10 seconds" warning, shows the "UID" errors, and returns to the Ubuntu logon screen. According to the error log, these errors pertain to seahorse-agent. 

At first I thought these errors were caused by improper AD authentication since they only happen to AD users (not local users). Now I'm thinking that seahorse-agent is starting up before the AD user has some other, primary local credentials and that some other process should be starting before seahorse.  Any ideas?

---

### Post by Charlotte18 on 2008-06-04
The exact error I'm getting is:

[INDENT]/etc/gdm/Xsession: Beginning session setup...

Setting IM through im-switch for locale=en_US.

Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default

(seahorse-agent:5733): GLib-WARNING **: getpwuid_r(): failed due to unknown user id (500)

(process:5733): GLib-WARNING **: getpwuid_r(): failed due to unknown user id (500)[/INDENT]

Anybody?

---

### Post by Oldsoldier2003 on 2008-06-04
by any chance are these migrated systems or is the AD server non Debian(based)?... user ids start at 1000 for debian based systems and 500 is the starting point of Redhat/fedora systems...

---

### Post by Charlotte18 on 2008-06-04
The AD server is Windows 2003. The difficulty I'm having is only happening on fresh installs of Hardy. Gutsy boxes  and Hardy boxes that were upgraded from Gutsy don't give the error.

---

