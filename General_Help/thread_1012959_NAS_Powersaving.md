---
title: "NAS Powersaving ?"
date: 2008-12-16
forum: General Help
---

### Post by BassKozz on 2008-12-16
I have an ubuntu box setup as my NAS (see sig for specs), and I was wondering if there is anything I can do to help save power?

Is it possible for this to go into sleep mode when it is not in use? or does mdadm require that my 3x drives (RAID5) stay spinning constantly?
Also if the computer goes into sleep mode, and a SAMBA access request wake it?

Any idea's on power saving are greatly appreciated.
-BassKozz

---

### Post by BassKozz on 2009-01-16
1 Month
:BUMP:

---

### Post by BassKozz on 2009-01-25
5 week
:bump:

C'mon, there has to be info on this, is there anyway to setup an Ubuntu machine to go into sleep mode when it's not needed and wake from sleep when there is a file access request (via eth) ?
Or some other similar settings?

Windows Home Servers have a feature to allow it to shutdown/startup at certain times: [http://www.wegotserved.co.uk/2008/07/14/power-saving-tips-for-your-windows-home-server/](http://www.wegotserved.co.uk/2008/07/14/power-saving-tips-for-your-windows-home-server/)
How can I setup something like this in ubuntu?

---

### Post by HermanAB on 2009-01-25
Well, you can read up on 'Wake on LAN' and you can read 'man hdparm' to see how to spin the drives down after 5 minutes of inactivity.  The only thing I would do is hdparm disk drive sleep.

Cheers,

Herman

---

### Post by BassKozz on 2009-02-02
Thanks HermanAB, but I've decided to go another route: [Need help creating an advanced shutdown script for powersaving?]("http://ubuntuforums.org/showthread.php?p=6662673")
hdparm scares me :p

---

### Post by agenthex on 2009-03-09
I, too, am interested in knowing what I can do to spin down an inactive RAID-5 array.  It was created using mdadm, and its location is /dev/md0.  Should I use hdparm on the individual devices (e.g. /dev/sda1 /dev/sdb1 /dev/sdc1) or should I use hdparm on the array identifier?  I really don't want to screw anything up and lose data (hence the RAID-5 array), but I do have two arrays and one is far more critical than the other.

---

### Post by fjgaude on 2009-03-11
> **agenthex said:**
> I, too, am interested in knowing what I can do to spin down an inactive RAID-5 array.  It was created using mdadm, and its location is /dev/md0.  Should I use hdparm on the individual devices (e.g. /dev/sda1 /dev/sdb1 /dev/sdc1) or should I use hdparm on the array identifier?  I really don't want to screw anything up and lose data (hence the RAID-5 array), but I do have two arrays and one is far more critical than the other.

I've never tried spinning down arrays... the law is to have backups for all important data. I have three, one online, another near-line, and finally, one off-line.

When I try things for the first time and cannot predict what the outcome will be is where those backups come into play. <smile>

---

### Post by BassKozz on 2009-03-11
> **agenthex said:**
> I, too, am interested in knowing what I can do to spin down an inactive RAID-5 array.  It was created using mdadm, and its location is /dev/md0.  Should I use hdparm on the individual devices (e.g. /dev/sda1 /dev/sdb1 /dev/sdc1) or should I use hdparm on the array identifier?  I really don't want to screw anything up and lose data (hence the RAID-5 array), but I do have two arrays and one is far more critical than the other.

agenthex,

If you don't need the server running 24/7 your probably better off shutting it down when not needed rather than spinning down the disks.  I've created a simple bash script that will help with automatically shutting it down when not needed:
[http://basskozz.wordpress.com/2009/02/03/advanced-shutdown-script-powersaving/](http://basskozz.wordpress.com/2009/02/03/advanced-shutdown-script-powersaving/)
also:
[http://basskozz.wordpress.com/2009/02/04/advanced-shutdown-script-part-2-check-for-running-services/](http://basskozz.wordpress.com/2009/02/04/advanced-shutdown-script-part-2-check-for-running-services/)

HTH, 
If however it is imparative that the server remains on 24/7 and you decide to give hdparm a shot please report back your results,
Thanks, Good Luck,
-BassKozz

---

