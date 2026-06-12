---
title: "Banshee is refusing to connect to iPod or Android devices"
date: 2013-07-06
forum: Gaming &amp; Leisure
---

### Post by cjsmall on 2013-07-06
Ubuntu 12.10 64-bit
Banshee 2.6.0

I recently moved all my music onto a Ubuntu system and am using Banshee to access it.  When I initially set this up, I connected my iPod Classic to the system and it recognized the device and synced up the music files.  However, I can no longer get Banshee to see the iPod.  I also tried attaching my Abanshee ndroid phone to see what would happen, but also nothing.  Nautilus sees both devices and each can be mounted/ejected there.  I have new music registered in Banshee, but these new files are never transferred to the iPod.

When I first connect my iPod, it shows the "connecting" message and then says that it is "syncing" for 5 seconds or so.  I think this is just something the iPod does upon every connection, as it displays this even though no music program is running.

Can anyone suggest some steps to debug this problem or some tricks for getting it to work.  Thanks.

---

### Post by cjsmall on 2013-07-17
If it will help get a response, I can boot Windows XP on this machine and the iPod connects and syncs with the latest version of iTunes, but still no signs of life with Banshee under Ubuntu.

---

### Post by silconsystem on 2013-07-18
It would be helpfull if you can post some log output, banshee will have complained about something 4 sure.
open a terminal:```
[FONT=Ubuntu Mono]banshee --debug > ~/banshee_debug[/FONT]
```
Now banshee will write a file called banshee_debug to your home directory.
Also starting banshee from the terminal could give some errors to see whats going on.

Banshees new versions should have support for IOS devices builtin. Firmware for IPad could be the problem but since your droid doesnt work either...

Also have a look at this: [http://askubuntu.com/questions/994/can-i-sync-with-my-ios4-device-such-as-iphone-4-and-ipad?lq=1](http://askubuntu.com/questions/994/can-i-sync-with-my-ios4-device-such-as-iphone-4-and-ipad?lq=1)


Cheers,


Rob

---

