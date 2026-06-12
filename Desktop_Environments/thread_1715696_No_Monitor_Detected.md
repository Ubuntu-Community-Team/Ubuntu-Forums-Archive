---
title: "No Monitor Detected"
date: 2011-03-27
forum: Desktop Environments
---

### Post by johnmata on 2011-03-27
i have been trucking along without issues for more than a year now, when out of the blue, this morning, i am getting a message on the monitors, "no monitor detected", and the status lights on the monitors are amber (as opposed to green).  i tried rebooting a few times, and at first everything looks normal; the status lights on the monitors go green, i see text on the screen during boot up, i see grub loading and all that, then suddenly the monitor status lights go to amber and i get the message on the screen "no monitor detected".

please help!

thanks,
john

---

### Post by ddoxey on 2011-03-27
The first thing I'd try is booting in recovery mode, and then run:

startx

That will probably fail. But there could be some useful information which you'll find in: /var/log/Xorg.0.log

And then if that doesn't help, you might try running:

dpkg-reconfigure xserver-xorg

And if that doesn't lead to anything... to be continued.

---

### Post by johnmata on 2011-03-27
startx yielded the following result:

[IMG]http://extreme42.com/ubuntuForumPics/1.jpg[/IMG]

and, dpkg-reconfigure xserver-xorg seemed uneventful.  rebooted into a "routine check of drive" with a friendly xubuntu splash screen.  updates to come....

---

### Post by johnmata on 2011-03-27
was looking promising, but ended with same result; amber status lights and monitor not detected.....

---

### Post by ddoxey on 2011-03-27
Perhaps reinstalling Xorg would do the trick. 

apt-get remove xserver-xorg
apt-get install xserver-xorg

---

