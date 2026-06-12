---
title: "Time zone not saved"
date: 2009-03-11
forum: Desktop Environments
---

### Post by lotech on 2009-03-11
I am running Ubuntu remix on USB boot, I don't know if this happen on a standard hard disk install. I installed NTP support for the time clock and it worked, but the time zone will not save and need to set it every time reboot.

---

### Post by larslarsson on 2009-05-20
Hi,
I'm running Intrepid off of a USB stick and have the exact the same problem. The Time Zone setting does not stick after a reboot (the time zone setting is empty). Setting Time Zone anew and synchronizing works.....
Thanks for any help!

---

### Post by larslarsson on 2009-05-24
Hi,
I tried the following (inspired by a fix for xorg.conf not being persisted when running off of a live USB stick), and it worked for me:

sudo su
cp /etc/localtime /etc/localtime.Oslo
echo "cp /etc/localtime.Oslo /etc/localtime" > resetTimeZone
mv resetTimeZone /etc/init.d
chmod +x /etc/init.d/resetTimeZone 
ln -s /etc/init.d/resetTimeZone /etc/rc2.d/S29resetTimeZone

You can use any file name instead of locatime.Oslo (I used it because that's my time zone).

Now, I have no idea if S29 on runlevel 2 is the optimal choice, maybe some Ubuntu guru can answer that.

Lars

---

