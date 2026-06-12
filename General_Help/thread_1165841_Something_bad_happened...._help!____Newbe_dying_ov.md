---
title: "Something bad happened.... help!    Newbe dying over here...."
date: 2009-05-21
forum: General Help
---

### Post by AaronMuslim on 2009-05-21
Something happened the last time I was logged into my ubuntu machine. I was trying to view my windows file system/partition in Natailus (spell check) and the mac looking hour glass came up and just stayed there. After a while of no activity or response to my request to view the partition I gave up, attempted to switch to the os. I couldn't log off and when it finnally gave some response I saw the shell prompt with a "I-have-no-name!@-desktop$". So, being the newbe I am I just thought a good restart and it's all good. WRONG. Now I can't boot into the gnome desktop and for some reason the ownership/accessiblity of my /etc/ folder has been changed. Now it's only rw- avaialible to root. I try sudo commands and it says they are unavailable. I'm guessing it's root, all of the ls -l info doesn't list users or groups it lists their numbers..1000 etc ... I can't log in as root because the password isn't being accepted and sudo commmands aren't working. every time I log in as my user (master) it drops the shell prompt to "I-have-no-name!@master-desktop$" and I can't move any of the files to mounted drives, access denied. WTF kind of options do I really have left?

---

### Post by AaronMuslim on 2009-05-21
A little more information:

Avahi mDNS-DNS fails to load on boot.

The first thing to come up is an error message saying:

"Cannot find or run the base script, running gnome failsafe
session instead"


.... And I can't click that away because the mouse is always frozen. I can alt-f1 into the desktop log-in prompt only to login-in to "no-name!@desktop$" with no privledges and not access to the root account ...... any ideas??

---

### Post by colau on 2009-05-21
May be,your account is deleted somehow.
See what happens after a fresh installation.

---

