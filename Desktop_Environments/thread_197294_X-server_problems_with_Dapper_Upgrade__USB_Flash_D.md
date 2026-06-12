---
title: "X-server problems with Dapper Upgrade / USB Flash Drive help?"
date: 2006-06-15
forum: Desktop Environments
---

### Post by mrstuie on 2006-06-15
Hi, I'm posting here because my upgrade went wrong!

On attempting to upgrade to the Dapper release candidate (on June 1st but before it was released - idiot!) something went wrong with the upgrade and when I rebooted xserver wouldn't work (=no GUI), and I couldn't reconfigure it automatically.

I don't think I have the know-how to sort it out and would probably rather start fresh, but I need to get my documents!

Can someone help with how to find the location of my USB stick so that I can copy my files across?

Thanks very much,

Newbie Mrstuie

---

### Post by wahman143 on 2006-06-15
Hi,
Your USB drive is going to be recognized as a SATA/SCSI drive, and therefore uses the node structure /dev/sdxy (where x is going to be 'a, b, c, etc' and y will be 1 if you only have one partiton on the drive).  So if you have NO SATA/SCSI drives on your system, it will probably be /dev/sda1...if you DO have SATA/SCSI drives on your box, it will be the last in the series (/dev/sdb1, /dev/sdc1, etc...).

Hope that helps ya,
W.

---

### Post by Sutekh on 2006-06-15
[quote=mrstuie]
Can someone help with how to find the location of my USB stick so that I can copy my files across?[/quote]

Try entering this command
```
tail -f /var/log/messages
```
Then plug in the USB, you should see a list of new messages appear.  They will detail the device node of the USB and the location of any mountable partitions (/dev/sdxy as wahman143 explained).

---

### Post by mrstuie on 2006-06-17
Great, thanks for your help - will get back with success or not! 

: )

---

