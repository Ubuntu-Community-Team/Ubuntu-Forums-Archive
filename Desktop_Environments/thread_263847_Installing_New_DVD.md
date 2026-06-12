---
title: "Installing New DVD"
date: 2006-09-23
forum: Desktop Environments
---

### Post by SuperMike on 2006-09-23
I want to install a new DVD in my Dell PC with Ubuntu. Is it just as easy as putting it in and rebooting, being autodetected, and it just works? Or do I have to run a command after that?

Second question - what about getting the extra utilities for it such that I can play movies on it?

---

### Post by CaveRat on 2006-09-23
> **SuperMike said:**
> I want to install a new DVD in my Dell PC with Ubuntu. Is it just as easy as putting it in and rebooting, being autodetected, and it just works? Or do I have to run a command after that?

Second question - what about getting the extra utilities for it such that I can play movies on it?

I personally would go ahead and install the drive and see what happens. You can always repost or use this existing post to report any problems.

Check out Automatix for the software needed for viewingmovies and such: [http://www.ubuntuforums.org/showthread.php?t=80295](http://www.ubuntuforums.org/showthread.php?t=80295)

---

### Post by SpacePony on 2006-09-23
If it doesn't do it automatically, it should be a simple matter of altering your /etc/fstab file. So:
```
sudo gedit /etc/fstab
```
I'll assume you know how to do that but if you need help with that just ask.

As for the dvd programs, I'll point you to that holy source, [http://ubuntuguide.org/wiki/Dapper#How_to_install_DVD_playback_capability](http://ubuntuguide.org/wiki/Dapper#How_to_install_DVD_playback_capability). 

The important part is libdvdcss2 which will require you have some respositories for apt-get/Synaptic that are not installed by default. [http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories) will tell you how to add those.

For programs I like xine and totem. Usually when one doesn't work the other does.

---

### Post by CaveRat on 2006-09-23
There you go. Seems I read that a while back but did not think of it. I thought of Automatix because of it's speed and simplicity.

---

