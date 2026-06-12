---
title: "(X)ubuntu - much slower then I thought. Can someone help me?"
date: 2007-01-30
forum: Desktop Environments
---

### Post by Apache777 on 2007-01-30
Hi, I'm pretty new in thel inux world (I'm using linux like 1 month) . I've tried some linux distros such as Slackware, Ubuntu, PCLinuxOS, but I really like Xubuntu. I don't like complicate desktop, so Xfce is right choice for me I thing. 

But here are some of my  problems.

My configuration is:
The latest Xubuntu (6.10)
Pentium D820
2Gb RAM
ATI X300, ATI RADEON 7000


I always thought that windows XP using more of my PC resources than linux and that linux will give me much more of my resources free for others applications and whole system will be faster.

but ... 

I've got 4 monitors (I know, I'm crazy but i  need this :D ) . I've configured everything just fine, but X process using about 15-25% of my CPU at ALL the time. In windows it was like 1% maybe 5% no more.  

And if I playing some video and working simultaneously, whole my system is sooo slow. I really don't know what it is. But it driving me crazy that linux using like 20%-30% of my CPU at all the time.

And one more question. I have belkin wireless card (bmc43**) and I'm using ndiswrapper driver but it seems like some times my connection just working perfectly and sometimes it's sooo slow. Like if I'm downloading something normal speed is 400kb/sec but sometimes it's just 20kb/sec. I don't know why :-( In windows I have not problem with those issues. :( 

But I really like linux and I would like to give it a chance because I don't want Vista and it's free :-) 

Or I was wrong with my thought that linux is faster OS and it using less of resources?

Thank you for any advice.
Apache:guitar:

---

### Post by K.Mandla on 2007-01-30
It is faster. Something's not right, and while I've never worked with a four-screen setup (?!) I think the problem might be video-related. Are you using ATI's proprietary drivers? And is this a Dell D820, or did you mean a different Pentium machine?

---

### Post by Apache777 on 2007-01-30
I'm using radeon drivers for my RADEON7000 card and ati drivers for X300 card. May be the problem that I can't make DRI working? I've tried to setup DRI but with no luck at all.  I have Dell dimension 5150 with Pentium D820 CPU

---

### Post by maxamillion on 2007-01-30
> **Apache777 said:**
> I'm using radeon drivers for my RADEON7000 card and ati drivers for X300 card. May be the problem that I can't make DRI working? I've tried to setup DRI but with no luck at all.  I have Dell dimension 5150 with Pentium D820 CPU

I assume you mean you are using the drivers called 'radeon' for the first card? .... If so, that is where your bottleneck is, same thing happens when using the 'nv' drivers on nvidia cards, the 'radeon' and 'nv' are both open source drivers that don't seem to play nice with dedicated cards.... you really need official drivers for cards with dedicated ram (non integrated) otherwise there is some sort of software emulation that bogs the system down (i don't know the specifics on why, just know from experience) so if you are able to find the driver version that will support the radeon7000 you will probably see an exponential performance gain.

I had an issue like this with an nvidia 5800 (or 6600, can't remember which machine it was) but the default was the 'nv' open source driver and the system was horribly unresponsive and was operating with 2gb of ram ... "sudo aptitude install nvidia-glx" and some editing to xorg.conf made it run like a champ.

---

### Post by Apache777 on 2007-01-30
yes I meant "radeon" drivers. Thank you very much. I'm gonna play with it and I will keep posting my progress.

---

### Post by maxamillion on 2007-01-30
Ok, I will check back from time to time and see how things are going ... I'm not entirely familiar with ATI cards, but I will help as much as I can.

---

### Post by Apache777 on 2007-01-30
Well, I really don't know what I'm doing wrong. For my Radeon7000 I have not found some other drivers. I've tried "radeon" and "ati" drivers for both my cards (and for X300 I've tried fglrx but it was not working correctly).

I don't know but xorg still takes like 20% of my cpu :( And it's little too much I thing. I like linux but it seems that I will have to migrate back to windows :-/

---

### Post by Cheizzz on 2007-01-31
You will need the official (closed source) ATI driver: fglrx.
Try installing the "xorg-driver-fglrx" package from the repository.

---

### Post by Apache777 on 2007-01-31
I've tried "fglrx" drivers with no luck :-(

---

### Post by nalmeth on 2007-01-31
I don't know much about ATI cards, but I must point out that you haven't posted much information on whats not working.

Whats wrong with fglrx drivers? X won't start? Don't get DRI? Whats up?

---

### Post by helloyo on 2007-01-31
> I've tried "fglrx" drivers with no luck :-(

this may work for you:

1. install the fglrx driver from the repositories
2. run the following commands:
- sudo aticonfig --initial
- sudo aticonfig --overlay-type=Xv
3. open up a text editor (sudo gedit /etc/X11/xorg.conf)
4. add the following to the end of the file and save
Section "Extensions"
        Option "Composite" "false"
EndSection
5. log out
6. restart xserver (CTRL + ALT + BACKSPACE)
7. log back in and hope for the best.

---

