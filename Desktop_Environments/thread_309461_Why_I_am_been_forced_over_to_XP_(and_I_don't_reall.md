---
title: "Why I am been forced over to XP (and I don't really like it)"
date: 2006-11-29
forum: Desktop Environments
---

### Post by jatos on 2006-11-29
Hi
I am currently been forced to use Windows XP, as I Ubuntu is too slow for my computer.

I have a laptop with the following specs

Efty Edge/Windows XP dual boot.
Intel Pentium @ 1ghz
RAM 256mb
40 gig HD with about 1gig of swap

I have Debian running on my sister laptop, at a reasonable peed and it only has a 266mhz processor with 328mb RAM. 

If Debian can run reasonably fast on that, why can't Ubuntu run fast on a laptop with the above specs? I might add I would use Debian instead if the packages where kept more up-to-date.

Also I would particuarly like to run OpenTTD on Ubuntu, however I have to run it on XP, Ubuntu's not fast enough to run it.

I am wondering, is there likely to be any effort been put into making Ubuntu run faster on all machines, as I really do not like haaving to use XP. Also I like my computer power to used mainly by my apps, not the OS.

---

### Post by shoagun on 2006-11-29
maybe try Xubuntu?

---

### Post by Lord Illidan on 2006-11-29
Else use another Linux distro: Zenwalk would be very nice on that pc.

---

### Post by jatos on 2006-11-29
> **shoagun said:**
> maybe try Xubuntu?

Happens regardless of WM, only thing that helps is switching to XFree86.

---

### Post by Mimsy on 2006-11-29
Have you tried Dapper? I run Dapper Drake on a laptop with a 1.2 GHz CPU, 256 MB of ram, and a 30 GB hard drive, and it is fast; a almost faster than my SO's brand new laptop that his employer lent him to use for business trips.

That's the only thing I can think of that might help, I am honestly baffled tht Ubuntu runs slowly on those specs.

/Mimsy

---

### Post by Lord Illidan on 2006-11-29
Also, perhaps you got something running you don't need.

---

### Post by shoagun on 2006-11-29
> **jatos said:**
> Happens regardless of WM, only thing that helps is switching to XFree86.

I'm not sure I understand what you mean.  I was referring to this:

[http://www.xubuntu.org/](http://www.xubuntu.org/)

Have you already tried Xubuntu instead of Ubuntu?  Given your specs, I would think Xubuntu would work fine.

---

### Post by jatos on 2006-11-29
Same speed regardless of what I have running, I have Apache/MySQL, but the problem existed prior to that. Also Mimsy, what programs are you using on your system? Firefox work at a decent providing I don't go todo any sites with a load of Ajax. However OOo and other more processor intensive programs that run fine on XP, and some other version of Linux don't on Ubuntu.

---

### Post by Mimsy on 2006-11-29
Most of the time I run Firefox and/or Open Office, and I tend to have Kopete running the background pretty much as soon as I am not doing school work. Kopete and Firefox are the only things I run side by side, I try not to multitask since the laptop gets very hot very quickly when I do. Edit: Open Office takes a long time to start, but once it's open I have no issues with it.

No antivirus, no firewall.

If you need more info, I'll be happy to give you a detailed list tonight when I'm home, and actually have access to the laptop. (At work right now.)

/Mimsy

---

### Post by shoagun on 2006-11-29
Also, as a side note, I would STRONGLY suggest using Dapper over Edgy.  I'm sure you can find much argument over the two in other threads, but honestly, in general, I think Dapper just runs smoother.

---

### Post by jatos on 2006-11-29
The main program I have a problem with is OpenTTD. My OS tends to get particuarly slow when I run both GTK and QT apps. When your at home btw, you would be able to go into a console and type ps -a straight after bootup mimsy? I interested to see what your last PID number is.

---

### Post by Mimsy on 2006-11-29
Give me a few hours, and I'll see what I can find out for you... :)

/Mimsy

---

### Post by d3v1ant_0n3 on 2006-11-29
You really should be able to run Ubuntu at a decent speed on that machine. More RAM is always useful if you can afford, if not, maybe increase the size of the swap partition? Or try a more lightweight DM (XCFE has already been suggested, there's also the really fast ones like IceWM, Fluxbox, etc).

And is all your hardware configured right? Gnome felt very slow to me at first with dapper, I later found out it was due to running vesa graphics drivers rather than the i810 ones for my graphics chipset.

---

### Post by Rodneyck on 2006-11-29
I can't believe Xubuntu would not be usable on your laptop, and fast. I installed it on an old laptop I was using as a coaster, just for kicks. It has half your specs, 128mb ram, 450 or 500 Pentium, and it was actually usable again.  

It originally shipped with Windows 98, a real peace of poo OS that was slow when I purchased it years ago. 

You have to install with the Xubuntu "alternative CD" which is a text based install, not the Live CD or it takes hours.  

If Xubuntu does not cut it, then I would guess that something else is wrong with your system.

---

### Post by Mimsy on 2006-11-29
Okay jatos, here you go:

> mimsy@Hawk:~$ ps -a
  PID TTY          TIME CMD
 5020 pts/0    00:00:00 ps
mimsy@Hawk:~$


I'm inclined to agree with the posters who have suggested there might be something wrong with your hardware. How old is the system? Is the hardware working flawlessly when you boot into XP?

/Mimsy

---

### Post by sysdrum on 2006-11-29
Here is a check list of system changes that may fix the speed issue.

1) Video settings if it is a nvidia driver load the nvidia legacy drivers or if ati then change to the ati binaries. but before any changes. make sure you are not just running the versa drivers. check the xorg.conf
2) Base Kernel (change it to match) the defualt is a i386 kern. that seems to cause a slow down on the p3's I have found so change it to the linux-generic kernel. That seemed to fix the issue on the 1ghz IBM thinkpad I setup with ubuntu.

3)ADD more ram. I am surprised you have not with xp. 512mb should help with system load on both sides. you have a gig of swap that is great but it is not always the best fix. look to see what you XP page file is. match your swap to that.

 

I am running

Athlon 1.2

1gig ram 

5gig swap

two 20gig in hardware raid

one 5gig drive for swap

128mb 5200 fx nvidia 4x

---

### Post by DarkN00b on 2006-11-30
> **jatos said:**
> Hi
I am currently been forced to use Windows XP, as I Ubuntu is too slow for my computer.

I have a laptop with the following specs

Efty Edge/Windows XP dual boot.
Intel Pentium @ 1ghz
RAM 256mb
40 gig HD with about 1gig of swap

I have Debian running on my sister laptop, at a reasonable peed and it only has a 266mhz processor with 328mb RAM. 

If Debian can run reasonably fast on that, why can't Ubuntu run fast on a laptop with the above specs? I might add I would use Debian instead if the packages where kept more up-to-date.

Also I would particuarly like to run OpenTTD on Ubuntu, however I have to run it on XP, Ubuntu's not fast enough to run it.

I am wondering, is there likely to be any effort been put into making Ubuntu run faster on all machines, as I really do not like haaving to use XP. Also I like my computer power to used mainly by my apps, not the OS.

I'm running an Edgy system specced almost exactly like yours. The only difference is that I have a 1.3 GHz proc. I ran Xubuntu Dapper on a 266 MHz desktop w/128 Megs of ram on a 40 Gig HD -- and it ran fast. I think you almost certainly have some hardware issues there.

---

### Post by bmathis on 2006-11-30
have you tried booting to an install CD and running memtest? You might have some ram issues that are causing your problems. Windows handles hardware differently and in my experience, Linux is more sensitive to hardware issues which is a good thing.

---

