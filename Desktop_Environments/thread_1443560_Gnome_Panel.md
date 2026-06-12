---
title: "Gnome Panel"
date: 2010-03-31
forum: Desktop Environments
---

### Post by amsz on 2010-03-31
Sorry if this has been repeated else where.
I have just started experiencing on boot up. instead of my usual wallpaper, I am faced with a black screen with a notification saying gnome power manager is not working? and to contact administrator. however I also have 3 dialogue boxes the first saying: **GConf error. failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or that you have stale NFS locks due to a system crash. Details- 1: Could not send message to GConf Daemon:Message did not recieve a reply (timeout by message bus)**the other 2 dialogue  hav e similar information:- *An error occured while loading or saving configuration information for gnome-panel (evoloution-alarm-notify). Some of your configuration settings may not work properly*

---

### Post by dusdus on 2010-03-31
Could you give some more information? Are you running 9.10 Karmic, or are you testing something? When did this error start, what did you do?

Os did a simple reboot solve it?

---

### Post by amsz on 2010-03-31
Running 9.10, error started after my computer just swiched itself off. rebooting keeps on bringing up the error screens

---

### Post by JustinR on 2010-03-31
Hi,

I've experienced this problem often, it usually happens to me if Ubuntu's root directory's have different file permissions (eg. the folder /var has different permissions other than root.) So look through your your filesystem directories and see if any of them are other than root.

I'm not sure if this is much help to you but reinstalling Ubuntu will fix the problem - I've never fixed it successfully.

Although an older thread this might be of some help:
[http://ubuntuforums.org/showthread.php?t=785012](http://ubuntuforums.org/showthread.php?t=785012)

Goodluck!

---

