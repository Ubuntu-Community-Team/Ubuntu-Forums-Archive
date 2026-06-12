---
title: "GDM won't load Openbox in UNR 9.10"
date: 2010-03-02
forum: Desktop Environments
---

### Post by sweekar on 2010-03-02
Guys,

I've been trying, unsuccessfully, to get open box to work on UNR 9.10.
I followed the following steps:

*I have removed gnome (apt-get remove libgnome2-0). 
* installed Openbox
*Re-installed gdm

When I boot, I get a blank screen and no openbox is loaded.

There is a bug report on the same ([https://bugs.launchpad.net/ubuntu/+source/openbox/+bug/272418](https://bugs.launchpad.net/ubuntu/+source/openbox/+bug/272418)), but none of the workarounds mentioned there seem to work for me :(

Any pointers?

Cheers,
Sweekar.

---

### Post by sweekar on 2010-03-02
Shameless bump :P

---

### Post by urukrama on 2010-03-03
Are you sure Openbox is not loaded? Openbox doesn't come with panels or wallpapers or icons on the desktop. You just get a blank screen; right click and you have your desktop menu.

Also, could you post your ~/.xsession-errors file? There might be some relevant information in there.

---

