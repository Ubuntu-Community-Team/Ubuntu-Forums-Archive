---
title: "Re sized drives and cannot boot"
date: 2009-03-23
forum: General Help
---

### Post by Acid_1 on 2009-03-23
As the topic may suggest, I re sized my hard drive, and set it from many partitions to sda5 for / (it was sda5 to begin with) and sda6 for /home/adam. Then I put sda7 for swap. I then proceeded to mount /dev/sda5 from the livecd still, and edited it's fstab (so gedit /media/disk/etc/fstab) and edited the lines so that it's using the correct mount points. I'm not using UUID. So, I reboot, and get the following error:

/etc/gdm/Xsession: Beginning session startup...
Setting IM through io-switch for local-en_CA.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
***temp: private socket dir: Permission denied

For the *** I think it is mkd but I can't read that part from the image. Any help would be very nice. Thanks :)

---

### Post by drs305 on 2009-03-24
A search of the error message "private socket dir: Permission denied" shows the solution might be the following, which would make sense if the /tmp directory can't be written to for some reason:
```
sudo chmod a+w /tmp 
```

---

### Post by Acid_1 on 2009-03-24
I'll give that a shot. Yes, /dev/sda11 was for /tmp. When I deleted the drive, I just thought it merged into /. I'll give that a shot.

---

### Post by Acid_1 on 2009-03-24
That solved it. Thank you. I'll give you the thanks when the forums are working correctly again.

---

