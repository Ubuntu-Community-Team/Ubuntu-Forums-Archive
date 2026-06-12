---
title: "mdadm - after reboot, array not found"
date: 2009-03-25
forum: General Help
---

### Post by seba22 on 2009-03-25
Hi,

I have problem, yesterday i'm talking about problems with my HDD ([http://ubuntuforums.org/showthread.php?t=1104896](http://ubuntuforums.org/showthread.php?t=1104896))

Now we bought 2 new HDD ( same series ) and  i want to put them into raid 1 using mdadm.

First step is, i wan't to try it on my desktop computer, next on my production server ( i need to know everything before shut down productions ever ;) )

So i grab this 2 disks, create partitions (same on both HDD).

Next i install mdadm ( first error found...) cpio: ./sbin/udevtrigger: No such file or directory.
[[img]http://www.bankfotek.pl/thumb/211014.jpeg[/img]](http://www.bankfotek.pl/view/211014)

But after that, mdadm start working.

I create array ( mirroring 1 ) sdc1 to sdb1 
Wait until rebuild process complete, I have got status "Clean"  now copy 8 gig of files to my new array,  ( very happy, everything working well) so I reboot machine.

And after reboot,  i cant acces to array, i cant add new array, i can do nothing... :/
When i want to list md0 information i'm getting:

[[img]http://www.bankfotek.pl/thumb/211018.jpeg[/img]](http://www.bankfotek.pl/view/211018)


When i  use dpgk-reconfigure mdadm 
everything start from begin, i can use array... but after restart... nothing work...

I'm trying dpkg-reconfigure after setup array, but won't help.

Do you have any idea ?

Please tell me, what do you need.

I'm using Ubuntu Interpid (8.10) kernel 2.6.27-14-generic

---

