---
title: "Kdeglobals not writable."
date: 2007-06-12
forum: Desktop Environments
---

### Post by markoloka on 2007-06-12
I tried to Lock Session as i usually do when i leave from kubuntu for a while. 
Today i started to get this error:

Kdesktop_lock

Will not save configuration.
Configuration file "/home/****/.kde/share/config/kdesktop_lockrc" not writable.
Configuration file "/home/****/.kde/share/config/kdeglobals" not writable.
Please contact your system administrator.

I tried to open firefox...nothing happens.
I tried to open ksystem logs viewer... same eroor pops up and that program crashes. 
I try to open kcontrol... same error again but kcontrol opens. 
I tried to open konqueror.... i get different error:
Could not start process Unable to create io-slave: Read-only file system.
Konqueror is empty no files, no folders, nothing....

So is my rights to my user files/folders changed??? How am i able to see them???
This kubuntu fiesty worked hour ago just fine. 
I'm getting fed up w/ problems in feisty. See that famous "can't access tty"-topic.

---

### Post by abn91c on 2008-03-29
in a terminal try 
sudo chown user:user /home/****/.kde/share/config/kdesktop_lockrc, replace user with your name

---

