---
title: "Dell Insisron mini 10 now internet wired or wireless"
date: 2010-11-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Doobster1 on 2010-11-04
Dell Inspiron mini 10 wireless and wired will no connect to the  internet. The wired network showed up as connected during the install but after reboot it will not connect.  
I have followed all of these instruction here

[http://ubuntuforums.org/showthread.php?p=10072830#post10072830](http://ubuntuforums.org/showthread.php?p=10072830#post10072830)

 and these:


[http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865)

                     Originally Posted by **jomtois**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8090292#post8090292")                 
                 [I]Perhaps this will help someone out there.

I was using Jaunty fine on my laptop (Dell e1705) with wireless working.    I installed 9.10 beta and could not get it to work.  In jaunty I was   using the Broadcom Wireless driver that showed up in System >   Administration > Hardware drivers.  

When I installed 9.10 as a fresh install from the live cd, it would list   only the Broadcom Wireless driver.  I kept choosing "Activate" and   entering my password, but it would never activate.  Having no network   connectivity, I was unable get any updates.

However this worked for me:

1) Open Synaptic Pacakage Manager
2) Ensure 9.10 LiveCd is in CD drive
3) Settings > Repositories > Ubuntu Software
4) Check the installable from cd and close
5) Refresh 
6) Search for "bcmwl-kernel-source"
7) Mark for installation
:cool: Install it
9) Reboot computer

That worked for me.  It was activated Hardware Drivers now.  Also, after   doing this (I think because dkms installed with it) now the graphics   drivers appeared in the Hardware Drivers scan, which hadn't before.

Basically, installing bcmwl-kernel-source was the key to success for me.  Handily, it is on the livecd.

Jon[/I]
                                 *I had similar issues, and resolved them exactly how you did.  My  wireless used to work out-of-the-box, but with 9.10 its never  worked  unless I've manually installed that package.*
_______________________________________________________________________


When I go to install the BCMWL even from a pen drive, it fails looking  for a CD.  I plugged in a portable HP CD drive and it doesn't even see  the drive.  I am brand new to Ubuntu so I am pretty clueless... Please  advise me what else I can do...

Thanks,
Bob

---

