---
title: "real player help"
date: 2005-12-23
forum: Desktop Environments
---

### Post by rfruth on 2005-12-23
New Breezy user here & when I use The Synaptic package manager to install Real Player I get the error ```
 The file /home/rp8_linux20_libc6_i386_cs2_rpm does not exist, or it is corrupt. You may have downloaded the wrong file, or put it in the wrong location. Please try again.
``` Help me get Real going !

---

### Post by bullfrog on 2005-12-24
dont know your problem.but try to do what i did. go back to synaptic do a complet uninstall. then go to add applications and type search then reinstall. hope it works for you.it did me. but you have to go to real player .com to finish   have a nice day   bullfrog;)

---

### Post by cjazz on 2005-12-24
All right, I'm extremely confused. You're trying to use Synaptic to install an *rpm* file? How is that possible? Can you give us a step-by-step description of what you did?

---

### Post by rfruth on 2005-12-24
After the package manager downloads RealPlayer the "Configuring realplayer" screen appears and the first prompt I get is "Real Player has been downloaded to where ?" (where *does* the package manager download files to) :confused:

---

### Post by NewbieNik on 2005-12-24
[QUOTE=rfruth]After the package manager downloads RealPlayer the "Configuring realplayer" screen appears and the first prompt I get is "Real Player has been downloaded to where ?" (where *does* the package manager download files to) :confused:[/QUOTE]

I found that the Synaptic RealPlayer is just an installer for an older version of RealPlayer (8) that you need to download seperately and ensure that it's the EXACT version.
I would search on the RealPlayer site for Linux and then follow the instructions provided. This will give you the latest version (10), but does involve a little work.

---

### Post by cjazz on 2005-12-24
Another option is to add either of the following two repositories to your /etc/apt/sources.list file, which allows you to directly install Real Player 10 through Synaptic or by "apt-get install":

deb [http://public.planetmirror.com/pub/plf/ubuntu/plf/](http://public.planetmirror.com/pub/plf/ubuntu/plf/) breezy free non-free
or
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sarge main

---

