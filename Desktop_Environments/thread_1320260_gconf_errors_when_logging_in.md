---
title: "gconf errors when logging in"
date: 2009-11-09
forum: Desktop Environments
---

### Post by Lord Erik on 2009-11-09
I have recently upgraded from 9.04 to 9.10 and it has worked fine with my profile.  However a second profile on the computer does not work.

When logging in I get the coloured background (looks like a fuzzy spotlight on black) and an old style error box 

>  An error occurred while loading or saving configuration information for evolution-alarm-notify. Some of your configuration settings may not work properly. 

I then get the defaul background and that's all.

daemon.log gives

>  /var/log/daemon.log:Nov 9 19:05:14 geek-school x-session-manager[3418]: WARNING: Error retrieving configuration key '/desktop/gnome/session/idle_delay': Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details - 1: Could not send message to gconf daemon: Message did not receive a reply (timeout by message bus)) 

there is no NFS file system (or lockfiles) nor is the computer set up to use TCP/IP to get config settings from elsewhere.

I have had a look through the forums and google, found a couple of references to this error but nothing on what it means or how I can fix it.  I'm not sure if the problem is gconf or evolution-alarm.

Any help would be appreciated.

---

