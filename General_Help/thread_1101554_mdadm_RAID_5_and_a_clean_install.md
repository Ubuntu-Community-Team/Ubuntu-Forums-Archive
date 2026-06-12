---
title: "mdadm RAID 5 and a clean install"
date: 2009-03-20
forum: General Help
---

### Post by scottac on 2009-03-20
I have been messing around wih mythbuntu 8.10 and I need to set up a RAID 5 aray for data storage (music, video, etc.). Now I am still pretty new to linux and I am sure that once I set up this raid array using mdadm I will be doing a couple of clean installs until I figure everything out.

I will be running the OS on a 20 gig partition on a 64 gig hard drive. the raid 5 array will be on 3 1 TB drives completely seperate from the OS. Now if I set up the raid 5 on those three drives and then later need to do a clean install on the separate drive will the data on the RAID 5 be secure. 

I am thinking that once the array is set up all i will need to do once I do a clean install is install mdadm on the new installation. Is it really this simple?

all help appreciated.

thanks

---

### Post by obscure_detour on 2009-03-20
Yes it is really that simple.  Once your array is created and functioning, you have the ability to do a clean install of anything you desire, given of course you install mdadm on the clean install.

So yes, you are correct, but I'll warn you like everyone else here, RAID is not a viable backup solution.  I have a very similar setup to yours and I've had no issues with mdadm and my RAID 5 array within the past year, but I still recommend backing up the data you care about most.

Hope this helps.  Here's some links that might help.

[http://blog.agdunn.net/?p=28](http://blog.agdunn.net/?p=28)
[http://tuxtraining.com/2008/11/04/setting-up-software-raid-in-ubuntu-server](http://tuxtraining.com/2008/11/04/setting-up-software-raid-in-ubuntu-server)
[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)
[http://bfish.xaedalus.net/?p=188](http://bfish.xaedalus.net/?p=188)

---

