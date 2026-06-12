---
title: "newbie install failing"
date: 2008-12-04
forum: General Help
---

### Post by deitripper on 2008-12-04
Have the newest version of Ubuntu on CD and attempting to install
to a desktop AMD Athlon 64 processor, gig of ram, ATI video card. The system has no OS at the moment.

Install stops at Busybox--initramfs-

-cannot create root/var/log: no such file
-mount: mounting /root/dev on /dev/.static/dev failed: no such file
-mount: mounting /sys on /root/sys failed: no such file
-mount: mounting /proc on /root/proc failed: no such file

Target filesysytem doesn't have /sbin/init

Ni init found. Try passing init= bootarg

Maybe you can point in the right direction. I've googled my problem but have not come up with anything. Is this a hardware problem? I suspect my hard drive as it is used.

Why would the target filesysytem NOT have /sbin/init?  Thanks.

---

### Post by Grolsche on 2008-12-04
Have you tried using ubuntu fromt he live cd to make sure it all works fine before you install?

If so did it work or when you say installing do you mean its not working from the live cd?

---

### Post by deitripper on 2008-12-04
I downloaded Ubuntu 8.10, made a CD and tried an install.

Not sure what you mean by trying a live CD first.

---

### Post by Grolsche on 2008-12-04
ok when u start the pc with the cd in, make sure your computer boots fromt he cd first.

Normally computers will automatically boot fromt eh cd but if it doesnt you can force it to by pressing F11 at the start.

Once it starts from the cd, you will get a list of choices. To start from Live cd it should be the top one.

What live cd does, is loads it into memory so you can make sure it works before spending time on the install.

Try that if you get stuck coem back.

---

### Post by deitripper on 2008-12-04
Thanks. I'll give that a try and see how it goes.

---

### Post by Grolsche on 2008-12-04
Not a problem. If livecd works out fine then we know where to start from, if you run in to problems with live cd then again we know where to start from.

---

### Post by deitripper on 2008-12-04
I tried choosing the first option in the menu but get exactly the same problem as I originally posted.

---

### Post by aggiemarine07 on 2008-12-04
If that fails as well reboot the system and select the "check disc for errors". I know in the past when I have installed a fresh system and had errors it was because of a bad disc or somehow an error got on the disc while it as being burned.

---

### Post by eternalnewbee on 2008-12-04
Wait a minute.
I had this problem a few days ago, and the solution was very strange. Hold on. Let me find the thread...

---

### Post by Grolsche on 2008-12-04
if your getting those problems, then i would first check that the cd disk is okay and doesnt contain any bad files. You can check the disk by choosing the options like you did for the livecd

---

### Post by eternalnewbee on 2008-12-04
OK. here's the thread:
[http://ubuntuforums.org/showthread.php?t=989553&page=5](http://ubuntuforums.org/showthread.php?t=989553&page=5)
Basically I took the RAM out, and put it back again.
But read the thread for yourself.
Caljohnsmith is my hero. Hope he can be yours, too.):P

---

### Post by deitripper on 2008-12-04
Thanks all for your help. I attempted to "check disk for errors" which led to nothing more than Busybox and the command prompt at "initramfs".

I think re-seating the ram is worth a try. Also will try installing with "no change to my computer" on a second machine which I can't do for a bit because I am downloading the Ubuntu Live CD for amd64 right now.

If it installs on the second computer then I assume the CD is OK.

Will keep working on it and thanks. By the way I ran memtest and all looks good there.

---

### Post by eternalnewbee on 2008-12-04
> Will keep working on it and thanks. By the way I ran memtest and all looks good there.
At least you won't have to go buy new RAM;)

---

