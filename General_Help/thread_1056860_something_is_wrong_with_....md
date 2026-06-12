---
title: "something is wrong with ..."
date: 2009-02-01
forum: General Help
---

### Post by sparkythewondersquid on 2009-02-01
I just bought a new computer compaq CQ60-224NR w/ 250 hdd 3G ram pentium dual core and I installed wubi/ kubuntu to test the thing out before doing a "native" install and things went wrong fast. Itwould not detect the wireless (no wlan0 listed) iwconfig showed only eth0 no wireless. I took it to work and plugged in to the eth0 there and every thing seemed fine I started th updates and thought I could just install ndiswapper and it would all be good. After an hour I checked on it the first update was not even done yet!! time remaining 7d 17h etc. this was not right so I booted back into windows thinking maybe the wubi install was borked I did a re-install and now the eth0 was not detected so I was mad at this point (glad I checked it out before the true install) so I put in the live disk no wireless there on my old gateway it detected every thing just fine in fact I have jaunty on that one now so I tried ubuntu insted fo kubuntu same thing and at the end of it all somehow the GRUB got onto the hard disk even after a system restore to the first boot Grub was still there when I selected kubuntu it started a true install but the partition part was blank could it be that newer computers are making it hard to use linux? now on knoppix it was fine with the disk. I did a complete restore to get rid of GRUB and am going to try again today if I cannot use linux on this machine it is of little use to me maybe exchange it for another gateway any one else hear of such problems?

---

### Post by Mud.Knee.Havoc on 2009-02-01
It's not necessary to reinstall Linux when things aren't working quite right (as it is with Windows, at least in my experience).

Wireless sometimes takes a bit of configuring before it works, which is common.  Hopefully each release will improve this bit by bit, as it seems to me to be the biggest problem facing Linux.

Your first problem (taking too long to update) could have just been your selection of mirror (ie. which server you were downloading updates from).  In this case, you could have just gone into Software Sources and picked another and it could have been faster.

Grub remained probably because it was installed in your Windows partition.

---

