---
title: "[SOLVED] Debian rocks on 32 MB RAM -- please help me."
date: 2008-07-25
forum: Debian
---

### Post by kagashe on 2008-07-25
After seeing the performance of Debian on my Laptop I installed it on my old desktop Pentium MMX 200 MHz 32 MB RAM (not expendable). I tried to install and run xorg but it did not work for my old monitor. I tried couple of Modelines in xorg.conf but could not succeed. Finally I installed xvesa and running it as root with following command.
> # xinit -- /usr/X11R6/bin/Xvesa -screen 640x480x16 -mouse /dev/ttyS1I have installed IceWM and created .xinitrc so that it starts with the above command.
Following is the output of free -m
         Total    used    free
Mem:      28       26       1 
-/+ buffers/cache  10      17
Swap      243       0     243

From ps aux I find that I could save on the memory by stopping tty2 tty3 tty4 tty5 tty6.

Please tell me how to do this.

kagashe

Following posted on July 28 2008
I could also succeed to run IceWM on xorg on this machine.
$ free -m
         Total    used    free
Mem:      28       26       2 
-/+ buffers/cache  11      17
Swap      243       1     243

There is hardly any difference in Xvesa and xorg (only 1 MB swap being used).

$ ps aux | wc -l
31

**Debian really rocks on 32 MB RAM.**

I have also configured the legacy ISA sound card. Read it [here]("http://ubuntuforums.org/showpost.php?p=5626748&postcount=18").

---

### Post by kagashe on 2008-07-25
> **kagashe said:**
> 
From ps aux I find that I could save on the memory by stopping tty2 tty3 tty4 tty5 tty6.

Please tell me how to do this.

kagasheI commented the getty lines for tty2 to tty6 in /etc/inittab
I have installed Kazehakase browser and it is really light. I am posting this from this browser on 32 MB RAM machine. As usual I have to wait for a page to load but once it loads I can scroll the page or type quickly as in this reply.
$ ps aux

root       638  0.0  0.5   2108   156 ?        S<s  01:39   0:02 udevd --daemon
root       988  0.0  0.0      0     0 ?        S<   01:40   0:00 [kgameportd]
root      1414  0.0  0.9   1656   272 ?        Ss   01:40   0:00 /sbin/syslogd
root      1422  0.0  0.6   1608   200 ?        Ss   01:40   0:00 /sbin/klogd -x
root      1444  0.0  0.9   1988   272 ?        Ss   01:40   0:00 /usr/sbin/cron
root      1466  0.0  0.6   2436   192 tty1     Ss   01:40   0:00 /bin/login -- 
kagashe   1474  0.0  0.5   3256   160 tty1     S    01:40   0:00 -bash
root      1484  0.0  0.6   2332   192 tty1     S    01:41   0:00 su
root      1485  0.0  0.5   2752   160 tty1     S    01:41   0:00 bash
root      1486  0.0  0.5   2708   160 tty1     S+   01:42   0:00 xinit -- /usr/X
root      1487  4.7  7.1   5864  2108 tty1     S<   01:42   2:02 /usr/X11R6/bin/
root      1490  1.6  5.0   8160  1484 tty1     S    01:42   0:41 icewm
root      1498 10.9 46.7 148060 13748 ?        Ssl  01:44   4:23 /usr/bin/kazeha
root      1568  0.0  0.0      0     0 ?        S    02:07   0:00 [pdflush]
root      1570  0.0  0.0      0     0 ?        S    02:08   0:00 [pdflush]
root      1580  2.2  8.0   5916  2364 ?        Ds   02:24   0:00 xterm
root      1584  0.7  5.0   2736  1472 pts/0    Ss   02:24   0:00 bash
root      1585 14.0  3.0   2264   888 pts/0    R+   02:24   0:00 ps aux

Kazehakase using less than 14 MB.
free -m
             total       used       free     shared    buffers     cached
Mem:            28         27          1          0          0          9
-/+ buffers/cache:         17         10
Swap:          243         34      209

kagashe

---

### Post by kerry_s on 2008-07-25
you could have just gone dsl linux. i would probably also have made the swap bigger, say 512 or 1g.

---

### Post by kagashe on 2008-07-26
> **kerry_s said:**
> you could have just gone dsl linux. i would probably also have made the swap bigger, say 512 or 1g.I generally use DSL on the desktop but experiment with others. I was using Ubuntu Dapper Drake with Xvesa on it which is now replaced by Debian Lenny with Xvesa.

kagashe

---

### Post by p_quarles on 2008-07-26
I did something similar with a 64 MB laptop a while back. It is very cool.

One of the reasons, by the way, that DSL performs slightly better on ancient hardware than even a stripped-down Debian is the 2.4 kernel. The difference in memory usage is negligible by modern standards, but for a 32 MB machine it does make a difference. You might try compiling one of those to get even more out of this old box.

---

### Post by kagashe on 2008-07-26
> **p_quarles said:**
> I did something similar with a 64 MB laptop a while back. It is very cool.

One of the reasons, by the way, that DSL performs slightly better on ancient hardware than even a stripped-down Debian is the 2.4 kernel. The difference in memory usage is negligible by modern standards, but for a 32 MB machine it does make a difference. You might try compiling one of those to get even more out of this old box.I don't think compiling the Kernel is necessary because Debian net-install automatically installed 486 Kernel on the desktop and 686 Kernel on the Laptop.

kagashe

---

### Post by pmlxuser on 2008-07-26
> **kagashe said:**
>  32 MB RAM .


Postal address please i can send you a few more modules i think i have them in old spare-parts machines. Oh for *** sake try to upgrade to 64MB ;)

---

### Post by kagashe on 2008-07-26
> **pmlxuser said:**
> Postal address please i can send you a few more modules i think i have them in old spare-parts machines. Oh for *** sake try to upgrade to 64MB ;)Thanks, but one of my friend already tried to add 32 MB. In fact it is already present in the hardware but does not show up in memory. If you know some thing about hardware please tell me how to make it work.

kagashe

---

### Post by p_quarles on 2008-07-26
> **kagashe said:**
> I don't think compiling the Kernel is necessary because Debian net-install automatically installed 486 Kernel on the desktop and 686 Kernel on the Laptop.

kagashe
I guess you didn't understand what I meant: the 2.4 kernel uses slightly less memory than the 2.6 kernel. Debian only uses the 2.6 kernel, therefore recompiling an older kernel might give you a slight performance boost.

No, it's not necessary, it was just a suggestion.

---

### Post by Canis familiaris on 2008-07-26
Umm... What is the bare minimum hardware specs to run a basic command line Linux 2.6 system?

---

### Post by Joeb454 on 2008-07-26
Probably not even 32Mb, but when you have that much RAM, you'd want to squeeze every last part of it :)

I know I would anyway...

---

### Post by kagashe on 2008-07-26
> **Anurag_panda said:**
> Umm... What is the bare minimum hardware specs to run a basic command line Linux 2.6 system?Previously I had installed Ubuntu Dapper Drake Cli on it but later versions of Ubuntu fail to install. The Debian installer says that:
> You must have at least 32 MB of RAM to use this Debian installer.

kagashe

---

### Post by tel93 on 2008-07-26
Use Sarge. That is my suggestion.

Older kernel + XFree86 (much faster than X.Org)

---

### Post by kagashe on 2008-07-26
> **tel93 said:**
> Use Sarge. That is my suggestion.

Older kernel + XFree86 (much faster than X.Org)Yes. I know that old version of any distribution would be better but Sarge security updates have been discontinued wef March 08.

I don't use Xorg on Lenny (in fact I could not) and use Xvesa (which is also said to be not secure and not maintained). I am looking for latest avatars of Xvesa like Xvfb Xfake etc.

I think Deli could be a better solution since there was a release recently.

kagashe

---

### Post by saulgoode on 2008-07-28
> **kagashe said:**
> Thanks, but one of my friend already tried to add 32 MB. In fact it is already present in the hardware but does not show up in memory. If you know some thing about hardware please tell me how to make it work.

Try adding a "mem=64M" to your kernel boot line. This does not always work, but it is worth a shot.

---

### Post by kagashe on 2008-07-28
I could also succeed to run IceWM on xorg on this machine.
$ free -m
Total used free
Mem: 28 26 2
-/+ buffers/cache 11 17
Swap 243 1 243

There is hardly any difference in Xvesa and xorg (only 1 MB swap being used).

$ ps aux | wc -l
31

**Debian really rocks on 32 MB RAM.**

kagashe

---

### Post by darrelljon on 2008-07-29
More noobs would use lightweight Debians if there was a prebuilt iso.

---

### Post by kagashe on 2008-08-20
This desktop has legacy ISA Yamaha opl3sa2 sound card. I had configured this card on Puppy Linux which has alsaconf utility by default. I have also configured it on Debian Lenny.

I installed alsa-utils package which contains alsaconf. After installations I got alsaconf in Debian menu. I clicked on it and had to enter the root password to start the wizard.

After sound card configuration I downloaded the command line CD player cdcd (it was dcd on earlier versions of Debian).

Now I am happily playing an audio CD and surfing through Kazehakase (or elinks) on Debian Lenny IceWM desktop on 32 MB RAM.

---

### Post by darrelljon on 2008-08-20
Anyone tried [The Little Debian]("http://bit.ly/PdbVo")?

---

### Post by mikjp on 2008-08-20
> **kerry_s said:**
> you could have just gone dsl linux. i would probably also have made the swap bigger, say 512 or 1g.

Uh, never!!

I use 40 MB swap with my laptop that has 40MB RAM. Try to imagine swapping half a gig with those hard drives. It would take the whole night...

The most important point is not to use any (or install) any software that really needs to swap. 

mikko

---

### Post by mikjp on 2008-08-20
> **kagashe said:**
> I could also succeed to run IceWM on xorg on this machine.


I've used IceWM, BlackBox & WindowMaker with 40MB RAM. Works ok.

mikko

---

### Post by DjBones on 2008-08-23
wow, im impressed. surprised your even dropping the luxury of IceWM on it too haha.
would you mind postin a memstat of it just for curiosity's sake?
also, you might be able to save a little bit of ram by halting a few processes like exim, portmap, yada yada with sysv-rc-config. but you probably already know about that haha.

---

### Post by kagashe on 2008-08-23
> **DjBones said:**
> wow, im impressed. surprised your even dropping the luxury of IceWM on it too haha.
would you mind postin a memstat of it just for curiosity's sake?
also, you might be able to save a little bit of ram by halting a few processes like exim, portmap, yada yada with sysv-rc-config. but you probably already know about that haha.
```
With Cli
$ free -m
		Total	used	free	shared	buffers	cached
Mem:		28	17	10	0	1	9
-/+ buffers/cache	6	21
Swap:		243	0	243

With xterm on IceWM
Mem:		28	27	1	0	0	14
-/+ buffers/cache	11	16
Swap:		243	0	243

With xterm and Kazehakase on IceWM
Mem:		28	27	1	0	0	14
-/+ buffers/cache	17	10
Swap:		243	10	232
```

No such processes are running. I had already posted ps aux [on this post]("http://ubuntuforums.org/showpost.php?p=5460046&postcount=2").

I replaced Debian Lenny by Deli Linux on this machine and find that the memory usage on Cli was 2 MB more in case of Debian but it was less by 2 MB on xterm+IceWM. However, the Netsurf web browser consumes much less than Kazehakase but Netsurf could not open orkut. I am trying to see why?

kagashe

---

### Post by kagashe on 2008-09-20
> **kagashe said:**
> I replaced Debian Lenny by Deli Linux on this machine and find that the memory usage on Cli was 2 MB more in case of Debian but it was less by 2 MB on xter +IceWM. However, the Netsurf web browser consumes much less than Kazehakase but Netsurf could not open orkut. I am trying to see why?

kagasheI tried Deli Linux on this machine for a few days but decided to switch back to Debian Lenny. I have installed Netsurf browser on Lenny and it behaves same as on Deli. The browser does not work on sites requiring javascript but it is good for Ubuntuforums and I am posting this using Netsurf on Debian Lenny.

kagashe

---

### Post by Mulenmar on 2008-09-30
> **darrelljon said:**
> More noobs would use lightweight Debians if there was a prebuilt iso.

I'm no noob, but I'd try a light Debian if someone made one. Who knows, maybe I'll make one for a college project. :grin:

---

