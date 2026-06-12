---
title: "TV Tuner keeps losing driver after reboot"
date: 2006-01-09
forum: Desktop Environments
---

### Post by endangst on 2006-01-09
I have a bt878 tv tuner card and forced it to card=16 tuner=28 using modprobe and it is listed as card=16 tuner=28 in the bttv directory.  

Previously I had no problem, but now after each reboot it will lose the driver and become a generic card again.

So, basically I have to unload/reload the driver each time I start Ubuntu like this:

endangst@ubuntu:~$ sudo rmmod bt878
endangst@ubuntu:~$ sudo rmmod bttv
endangst@ubuntu:~$ sudo modprobe -r bttv
endangst@ubuntu:~$ sudo modprobe bttv card=16 tuner=28

Can anyone help?  I can't figure out why this started happening.

Thanks!

---

### Post by zoiks on 2006-01-09
I believe you can get what you want by editing /etc/modprobe.conf.  There, you can set options that are used when a module is loaded.  A line like "options <module> <option>" I think is what you're looking for.  Check out man modprobe.conf.

---

### Post by endangst on 2006-01-09
> I believe you can get what you want by editing /etc/modprobe.conf. There, you can set options that are used when a module is loaded. A line like "options <module> <option>" I think is what you're looking for. Check out man modprobe.conf.

Is this the proper form? 

options bttv card=16 tuner=28

I put that in /etc/modprobe.conf just now.

---

### Post by zoiks on 2006-01-09
[QUOTE=endangst]Is this the proper form? 

options bttv card=16 tuner=28

I put that in /etc/modprobe.conf just now.[/QUOTE]
I believe so.  Restart and see what happens.

---

