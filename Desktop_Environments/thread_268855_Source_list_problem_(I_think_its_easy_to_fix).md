---
title: "Source list problem (I think its easy to fix)"
date: 2006-09-30
forum: Desktop Environments
---

### Post by Ebzero on 2006-09-30
Alright i was just using my Ubuntu and i loved it just intsalled it today but i attempted to install my video card drivers (ATI) and when i restart it its all messed up so i was wondering if any one knows a command for terminal that will give me a fresh Source List with out having to retype one Much thanks
-Rob
Ubuntu version 6.06.1

---

### Post by ardchoille on 2006-09-30
Try this out:

[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

It's an Ubuntu sources.list generator website :)

---

### Post by Ebzero on 2006-09-30
Thats a very usefull sight and ill keep that one in mind for the future but what i am looking for is a command that will automaticly get me a fresh Ubuntu vs 6.06.1 source preferably with the security updates and stuff :neutral:

---

### Post by kerry_s on 2006-09-30
I think your asking for the wrong thing. The sources.list is for the repos, I thing what you need is to setup your xorg.conf for the ati driver.

sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by ardchoille on 2006-10-01
> **kerry_s said:**
> I think your asking for the wrong thing. The sources.list is for the repos, I thing what you need is to setup your xorg.conf for the ati driver.

sudo dpkg-reconfigure -phigh xserver-xorg

Ah, ok, I misunderstood then. Sorry about that Ebzero.

---

