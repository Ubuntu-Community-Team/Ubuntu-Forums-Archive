---
title: "Help me fix my 2min boot time"
date: 2009-02-02
forum: General Help
---

### Post by gfd on 2009-02-02
I'm attaching my bootchart logs hoping that someone will be able to help me make sense of it and fix this ridiculous boot time.

Boot time: 2m 7secs
System:
Ubuntu 8.10
Intel Core 2 Duo T7200 @ 2.00GHz
2GB Memory
GeForce Go 7300 512MB

Thanks in advance

---

### Post by Yashiro on 2009-02-02
Image is too scaled down to be readable.

Yeah some javascript weirdness with the forums stupid lightbox code.

---

### Post by gfd on 2009-02-03
> **Yashiro said:**
> Image is too scaled down to be readable.

Either your browser or the javascript photo script scaled it down to fit the viewport. Click on it again to view at the proper size.

The resolution was not scaled at all to specifically avoid being unreadable.

The actual resolution is 3150x2685.

Thanks for taking a look.

---

### Post by run1206 on 2009-02-03
i had the same problem on my Toshiba laptop.  When executing the networking process, it stayed longer than expected. The only way i shortened my time was to turn off all the other unneeded processes...
```
sudo apt-get install sysv-rc-conf
```
not sure if you've used this before, but when opened in a terminal...
```
sudo sysv-rc-conf
```
you will see all the processes running on your comp.  uncheck the ones you don't use.  check the forums cuz someone has written which processes you need and which ones you don't.  Regarding the "Networking" process, i shut off that process and turned it on after logging into GNOME, hope that might work for you as well.

---

### Post by mb_webguy on 2009-02-03
Since you have a multi-core processor, you can set the boot process to use concurrency, which may significantly decrease boot time.

In the terminal, type "sudo gedit /etc/init.d/rc" and look for the line "CONCURRENCY=none".  Change this to "CONCURRENCY=shell", then save and exit.  The very next time you boot may not be much faster, but subsequent boots should be.  I have the same processor as you, and doing this cut my boot time significantly, to the point that booting is faster than login.

---

### Post by Yashiro on 2009-02-03
Do you use a wireless connection?
I assume you get an automatic ip address?
Do you mount any ntfs volumes at boot?


Seems like a network issue. I assume your PC basically goes dead for about a minute then kicks into life.

---

### Post by gfd on 2009-02-04
Problem solved!

It was a networking issue as suggested.

I set the start-up manager to show text during boot and I saw that, as Yashiro pointed out, the boot process seemed to pause for about a minute at "configuring network interfaces".

I have a wireless internet connection so I tried different things such as setting a static IP ([excellent how to]("http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/")), setting different nameservers and then even removing Network Manager altogether and installing wicd manager instead.

The problem though, was with my inactive wired connection.
The manual setting of a static IP for my wired connection fixed it.
Disabling it altogether would've probably solved my problem too.
I think that during boot the /etc/network/interfaces was read and that it had trouble resolving/assigning an IP to the listed wired eth0 interface.

After adding a static IP manually in /etc/network/interfaces the pause during boot disappeared and I can still use my wireless connection.

Now, in regards to your comments.

> **run1206 said:**
> ```
sudo sysv-rc-conf
```
I didn't know of this. I'll be using it, to improve my boot time even more.

> **mb_webguy said:**
> In the terminal, type "sudo gedit /etc/init.d/rc" and look for the line "CONCURRENCY=none". Change this to "CONCURRENCY=shell", then save and exit.
This is an excellent tip. I can't even imagine how many people would easily benefit from this but just don't know about it....

Anyway, a big thanks to everybody

---

### Post by run1206 on 2009-02-04
ironically, i had the same problem a while back.  my wired connection wasn't connecting so it seemed like the bootup would "hang" for about 50 seconds :( 
i installed wicd then, but i'm still with Network Manager and no problems so far :)

and yeah, sysv-rc-conf is pretty good with turning off processes you don't use during bootup. 
here's the tutorial from the forums...
[http://ubuntuforums.org/showthread.php?t=89491&highlight=sysv-rc-conf](http://ubuntuforums.org/showthread.php?t=89491&highlight=sysv-rc-conf)

an alternative to sysv-rc-conf is BUM (boot-up manager)
```
sudo apt-get install bum
```
BUM is the same, but is a GUI.

---

### Post by gfd on 2009-02-04
> **run1206 said:**
> ironically, i had the same problem a while back.  my wired connection wasn't connecting so it seemed like the bootup would "hang" for about 50 seconds :(
You said that you had this problem on a Toshiba laptop!
I'm on a Toshiba Satellite A200-10W.
This might be related Toshiba specific hardware. 
I just thought I'd mention it in case someone else is having the same problem.

> **run1206 said:**
> i installed wicd then, but i'm still with Network Manager and no problems so far :)

I'm still using wicd although I'm thinking of going back to network manager since it was not the problem.

> **run1206 said:**
> 
here's the tutorial from the forums...
[http://ubuntuforums.org/showthread.php?t=89491&highlight=sysv-rc-conf](http://ubuntuforums.org/showthread.php?t=89491&highlight=sysv-rc-conf)

an alternative to sysv-rc-conf is BUM (boot-up manager)
```
sudo apt-get install bum
```
BUM is the same, but is a GUI.

Thanks again run1206, I'll be definitely looking into this.

---

