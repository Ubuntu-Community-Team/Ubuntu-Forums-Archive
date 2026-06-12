---
title: "xorg.conf in 9.10 xubuntu"
date: 2010-04-12
forum: Desktop Environments
---

### Post by BJ_Covert_Action on 2010-04-12
Howdy Y'all,

I just installed xubuntu 9.10 on an old computer that I am hooking up to my rear screen projection (yeah, I'm old school) TV in my living room. The computer has an ASUS made Radeon 9600 SE video card in it. Upon initial install, xubuntu seems to have detected the video card alright and is running the open source driver (the only driver option available for the 9600 so far as I can tell). However, it does not seem to be able to launch an X environment that is displayable on the old TV.

Right now, I have a second monitor hooked up, via VGA, so that I can operate on the filesystem and such. However, upon some inspection, it doesn't appear that I have any xorg.conf file in my /etc/X11 directory. I don't know if that's because 9.10 doesn't use that setup anymore or if it just hasn't been made yet. I ran a...

```
sudo find / -name "xorg.conf"
```

...command, but it didn't turn anything up. As such, I've started brewing my own xorg.conf file according to [this discussion on opensource drivers.](https://help.ubuntu.com/community/RadeonDriver) However, that guide doesn't say anything about whether or not xubuntu keeps the xorg.conf file in the same place as ubuntu. For that matter, it also doesn't say if I need to do anything to enable reading and loading of my xorg.conf file.

So, my question, does xorg.conf usually live in /etc/X11 as it does in ubuntu? Also, do I need to do anything special to enable its reading in 9.10 xubuntu?

Thanks ahead of time for any help. 

Best of luck all.

---

### Post by iponeverything on 2010-04-12
[http://superuser.com/questions/51248/where-is-the-xorg-conf-file-in-karmic-koala-ubuntu-9-10](http://superuser.com/questions/51248/where-is-the-xorg-conf-file-in-karmic-koala-ubuntu-9-10)

---

### Post by BJ_Covert_Action on 2010-04-12
Thank you sir.

---

