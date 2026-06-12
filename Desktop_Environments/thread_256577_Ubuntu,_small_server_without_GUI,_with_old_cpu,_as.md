---
title: "Ubuntu, small server without GUI, with old cpu, as file server and running amule"
date: 2006-09-13
forum: Desktop Environments
---

### Post by fabri00 on 2006-09-13
I have a main pc at home running Ubuntu 6.06 (after some helps from this forum to make it fully working !), and a small lan with an adsl modem/router/firewall.

The idea is to have a smaller pc (I have a small sized P3 1.000 Mhz with 256 mb ram) running amule continuosly, to be used also as file storage; it must be used without monitor, keybord and mouse; maybe it can even be placed in a different room in ordxer to avoid noise.

I've tested vnc and several clones of it, but the small pc seems to be overloaded; I tested Ubuntu 6.06 and also Xubuntu with similar results: the system is too slow to be used.

The idea is to have Ubuntu in the small pc without GUI, in order to have a lighter system, and to adminstrate and use it from the main pc trhough a browser interface.

...Unfotunately i dont have an idea about how to do it, as well as I'm not familiar with linux/ubuntu without GUI.

Any help or tutorial will be very much apreciated.

Thanks.

---

### Post by tomBorgia on 2006-09-13
Hi Fabri, As far as I know amule has a web admin option so you could install it on your server and just connect to that with your browser - I think you would need to have a monitor / VNC set up initially to start amule... I just tried to run it from the command line and it didn't like not having gnome/kde...so try this [http://www.amule.org/wiki/index.php/AMuleCMD]("http://www.amule.org/wiki/index.php/AMuleCMD")
If you need to admin the server SSH is the easiest way and is switched on by default for a ubuntu-server install...

So ideally, install ubuntu-install (works nice on a low-spec system cuz it doesnt have a gui)... install amulecmd, use ssh to start / stop amule etc... and use ftp / nfs to get at your downloads... there are howto's on ssh/ftp/nfs on this site somewhere...

---

### Post by tomBorgia on 2006-09-13
sorry meant install ubuntu-server...

---

### Post by fabri00 on 2006-09-13
Thanks tomBorgia.

---

### Post by TSMJ on 2006-09-13
I'd suggest at least 512Mb RAM to run KDE (/Gnome) - that may have been your problem.

I'm pretty sure SSH is not running by default on ubuntu server. `Apt-get install ssh` fixes that though.

If your P2P client requires a GUI to work, you can install KDE or whatever, but not have it start on boot - AFAIK all you need are the files installed on your system and you can get VNC sessions working, it doesn't have to be running.

---

### Post by tomBorgia on 2006-09-13
My 256Mb / 2gHz pc runs gnome fine... wouldn't fancy anything less tho :D

---

### Post by fabri00 on 2006-09-22
I've upgradet memory to 512, but it is still slow, probably due to the cpu limits.

I'm now working without GUI, and it is fine; system goes very well.

Thanks to all.

---

### Post by reclusivemonkey on 2006-09-22
> **fabri00 said:**
> I've upgradet memory to 512, but it is still slow, probably due to the cpu limits.

I'm now working without GUI, and it is fine; system goes very well.

Thanks to all.

My "server" has much lower spec than yours and runs fine (running apache for my website and a Counter-Strike server), however it is running Slackware without X. To determine where your bottleneck is you should look at

```

free -h

```

which will tell you how much memory is being used. Also

```

tload

```

will show you in a real time graph what sort of load your machine is under. If you are using it as a file server, and there is a lot of disk activity, then it could well be that your hard drive is the bottleneck, especially if its only a 5400 rpm hard drive. If you can upgrade, a 7200 rpm hard drive with a more than 2Mb cache may well help.

HTH

---

### Post by enopepsoo on 2006-09-22
> **reclusivemonkey said:**
> 
```

free -h

```

which will tell you how much memory is being used. Also


free -h does not do anything for me.:-({|=

---

### Post by reclusivemonkey on 2006-09-22
> **enopepsoo said:**
> free -h does not do anything for me.:-({|=

meh, I am at work, I may have forgotten the syntax. I thought -h gave it in human readable format (i.e. megabytes, gigabytes, etc.). Try free on its own; if that doesn't work then you don't have free installed. I think free -m should give it in megabytes

---

### Post by enopepsoo on 2006-09-22
Cool, thanks.  I just hoped there was some cool hidden feature that I was missing out on. :tongue:

---

