---
title: "webcams swap device names at boot"
date: 2009-03-01
forum: General Help
---

### Post by ubuntwinkel on 2009-03-01
I really tried to find where this might best be presented, and found that while everywhere was almost appropriate, nowhere was better than 'General Help.'  So here goes:

I have two webcams attached to my desktop mongrel box.  I have a combination of cron jobs and bluproximity scripts set up to start 'motion' whenever me (and my cell phone) leave the house.  Motion accesses the webcams as either /dev/video0 or as /dev/video1.  One cam is a USB cam, and the other is a video capture PCI card.  Each has different configurations for motion in motion's configuration files, thread1.conf and thread2.conf.  

The problem is that every time I reboot, the cams swap device names.  i.e.: I have PCIcam configured in thread1.conf as /dev/video0, and USBcam configured in thread2.conf as /dev/video1.  Then I reboot and when motion tries to start it dies because it is trying to use the USBcam config to interact with the PCIcam.  

In a nutshell:
```

PCIcam=/dev/video0        <<  R E -  >>        USBcam=/dev/video0
USBcam=/dev/video1        << B O O T >>        PCIcam=/dev/video1

```

I have fantasized writing an agonizingly long script which might 'parse' which was which after boot time, and then surgically alter each config file to suit.  But that seems way more trouble than necessary.  

Isn't there an easy way of telling my system that at each and every boot, the PCIcam is to be always linked to /dev/video0 and likewise, the USBcam to /dev/video1?  

Praying you who have an answer have read this far.

---

