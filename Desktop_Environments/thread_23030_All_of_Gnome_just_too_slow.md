---
title: "All of Gnome just too slow"
date: 2005-03-30
forum: Desktop Environments
---

### Post by Quest-Master on 2005-03-30
Applications, menus, and just about everything else in Gnome is unbearably slow. It takes a grand and exact 10 seconds for the main Gnome menu to open up, and another 10 seconds to open any other application, give or take 2-3. And, it has gotten to the point where I've gone back to using Windows XP, where most of the apps. that perform the same task take about 2-5 seconds to start.

I've been told by many on IRC to simply go to KDE since my computer should be able to run it perfectly, or XFCE if it performs badly on that as well. But, not only is the desktop the problem, but so are the applications. I know KDE has a different set of apps., but.. XFCE doesn't.

Btw, I have a 2.2Ghz Celeron, 256 MB RAM, and an Intel Integrated Graphics Extreme  Card (know that that doesn't affect anything, but just listed it for the heck of it).

Yeah. I really want to go back to Ubuntu but.. it's pretty unbearable right now. :(

---

### Post by Nis on 2005-03-30
[QUOTE=Quest-Master]Applications, menus, and just about everything else in Gnome is unbearably slow. It takes a grand and exact 10 seconds for the main Gnome menu to open up, and another 10 seconds to open any other application, give or take 2-3. And, it has gotten to the point where I've gone back to using Windows XP, where most of the apps. that perform the same task take about 2-5 seconds to start.

I've been told by many on IRC to simply go to KDE since my computer should be able to run it perfectly, or XFCE if it performs badly on that as well. But, not only is the desktop the problem, but so are the applications. I know KDE has a different set of apps., but.. XFCE doesn't.

Btw, I have a 2.2Ghz Celeron, 256 MB RAM, and an Intel Integrated Graphics Extreme  Card (know that that doesn't affect anything, but just listed it for the heck of it).

Yeah. I really want to go back to Ubuntu but.. it's pretty unbearable right now. :([/QUOTE]
 It sounds like DMA is not being enabled for your drive.  No DMA and everything seems reeeeaaaallllyyyy slow.  Try running
```

sudo hdparm -d1 /dev/hda

```
from a terminal and see if performance improves.  If so then you'll have to setup /etc/hdparm.conf to automatically turn on DMA.  If not (such as you get an error from hdparm) support for your IDE controller might not be available or least not compiled in the kernel or as a kernel module.  I know this sounds pretty technical and Ubuntu really shouldn't be.  You might have just found a bug though.

---

### Post by Quest-Master on 2005-03-30
[QUOTE=Nis]It sounds like DMA is not being enabled for your drive.  No DMA and everything seems reeeeaaaallllyyyy slow.  Try running
```

sudo hdparm -d1 /dev/hda

```
from a terminal and see if performance improves.  If so then you'll have to setup /etc/hdparm.conf to automatically turn on DMA.  If not (such as you get an error from hdparm) support for your IDE controller might not be available or least not compiled in the kernel or as a kernel module.  I know this sounds pretty technical and Ubuntu really shouldn't be.  You might have just found a bug though.[/QUOTE]
 Someone asked me to do this exact thing on IRC, and it appeared that hdparm was already enabled. It might've been turned off or something in the meantime, but.. yeah, I'll try again.

---

### Post by maqi on 2005-03-30
Interesting post ... I have always used KDE until I decided to give ubuntu a go. Figured I'd give GNOME a go at the same time. My experience is that GNOME is a lot faster than KDE. Both are considered to be bloated and slow by many linux users which is why they use, eg,  Xfce or Fluxbox, etc. 

Put it this way ... If you're having trouble running GNOME you're going to have trouble running KDE. Your machine *should* run either desktop easily so it is likely to be a configuration issue of some sort.

Please let us know if the hdparm tweak works :)

---

### Post by nix4me on 2005-03-30
I would have to disagree.  I have been running kde distros for the past 3 years and ubuntu with gnome is definately faster.
 
There must be something else wrong, beacause its definately not gnome.
 
Granted, I use a p4 2.8 with 512.  Maybe you should add more memory.  256meg is not enough for any os these days.
 
Mark

---

### Post by bored2k on 2005-03-30
**Quest-Master:** Try prelinking:
> Prelink is in universe. I use it on my Ubuntu system without issues,
but do google about Prelink and do your research before trying it out.

How to enable prelink:

1. Activate Ubuntu universe sources. The procedure is well-documented by Ubuntu.
2. use apt-get or synaptic to install prelink.
3. Open /etc/default/prelink with your favorite editor, as sudo/root.
4. Change PRELINKING=unknown from unknown to yes.
5. Adjust the other options if you know what the heck you're doing.
Defaults work well.
6. To start the first prelink (the longest one!), run sudo
/etc/cron.daily/prelink

In the future, prelink performs a quick prelink (a less-than-1-minute
procedure on most systems) daily, usually at midnight. Every 14 days,
or whatever you changed it to be, a full prelink will run.

If you just did a major apt-get upgrade that changed systemwide
libraries (i.e. libc6, glibc, major gnome/X libs, etc etc etc) and
experience cryptic errors about libs, rerun step 6.

To undo prelink, change step 4 from yes to no, then rerun step 6.

---

### Post by Quest-Master on 2005-03-30
Hehe, I've tried prelinking too.. in a different way from what you listed though. I'll try that now.

Also, someone says the Gnome menu can take a while to load if you do not have memory caching enabled. Does anyone know how I can enable this?

---

### Post by maqi on 2005-03-30
[QUOTE=maqi]My experience is that GNOME is a lot faster than KDE.[/QUOTE]

[QUOTE=nix4me]I would have to disagree.  I have been running kde distros for the past 3 years and ubuntu with gnome is definately faster.[/QUOTE]

:confused:

---

### Post by Nis on 2005-03-30
The speed issue between GNOME and KDE is really dependent on a lot of things.  KDE on Slackware is blazingly fast, but GNOME on Ubuntu seems almost as fast.  I think a lot of that has to do with user perception.  As for prelinking: it should help apps start up faster.  I still think the lack of DMA is the culprit.  Quest-Master, could you please post the output of the commands below:
```

sudo -s <now input your password>
for disc in `ls /dev/hd?`; do hdparm $disc; done

```
The ` in the code is a backtick.  It is located just left of '1' on a US keyboard (same key as ~).  It is very important that backticks are used in the code above.

After you get back with this we'll work on getting GNOME up to speed.

---

### Post by Quest-Master on 2005-03-30
> **Nis]The speed issue between GNOME and KDE is really dependent on a lot of things.  KDE on Slackware is blazingly fast, but GNOME on Ubuntu seems almost as fast.  I think a lot of that has to do with user perception.  As for prelinking: it should help apps start up faster.  I still think the lack of DMA is the culprit.  Quest-Master, could you please post the output of the commands below:
```

sudo -s <now input your password>
for disc in `ls /dev/hd?` said:**
> 
 
[quote]root@ubuntu:~ # for disc in `ls /dev/hd?`; do hdparm $disc; done

/dev/hda:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 65535/16/63, sectors = 40020664320, start = 0

/dev/hdc:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument


hda is my main hard drive with everything on it. I have no clue frankly what hdc is, hehe. I've also done another cron prelink, and hdparm.

Anyone still know about the memory caching thing for the Gnome menu?

---

### Post by Nis on 2005-03-30
Alright.  DMA is enabled but a few other settings are worrisome.  Try running the first command and post the output here.  Then try running the second to enable some settings.

First command:
```

hdparm -i /dev/hda

```
Second command:
```

hdparm -d1 -m16 -c1

```

---

### Post by bored2k on 2005-03-30
Intrigued ... wonder what Nis is thinking ...

---

### Post by Quest-Master on 2005-03-30
> /dev/hda:

 Model=WDC WD400EB-00CPF0, FwRev=06.04G06, SerialNo=WD-WCAATA872348
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=16383/16/63, TrkSize=57600, SectSize=600, ECCbytes=40
 BuffType=DualPortCache, BuffSize=2048kB, MaxMultSect=16, MultSect=off
 CurCHS=17475/15/63, CurSects=16513875, LBA=yes, LBAsects=78165360
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: device does not report version:

 * signifies the current active mode


For the first command. I had to add "/dev/hda" at the end of my second command, and it worked as well. I have been noticing a slight increase in speed systemwide, happy to say. :) Still a slow Gnome though.

---

### Post by Nis on 2005-03-30
[QUOTE=Quest-Master]For the first command. I had to add "/dev/hda" at the end of my second command, and it worked as well. I have been noticing a slight increase in speed systemwide, happy to say. :) Still a slow Gnome though.[/QUOTE]
 Interesting.  Your drive is like mine; we both have WD just different models. :)

I couldn't see anything in the info you posted that might change things anymore hdparm wise, I think.  If you want you can put this into /etc/hdparm.conf to have these settings at boot:
```

/dev/hda {
        mult_sect_io = 16
        io32_support = 1
        dma = on
        read_ahead_sect = 256
}

```

Now what can we do to get further speed?  Have you tried installing the i686 optimized kernel?

---

### Post by bored2k on 2005-03-30
I still see no reason for gnome going slow on him ..

---

### Post by Quest-Master on 2005-03-30
Programs are still taking a bit to load up, especially Firefox which I've given up for Galeon, but it's pretty much fine now. :)

I should consider getting some new RAM I guess sometime.

---

### Post by Nis on 2005-03-30
[QUOTE=bored2k]I still see no reason for gnome going slow on him ..[/QUOTE]
 I don't either.  His symptoms he described were very similar to when I had not compiled support for my IDE controller into a kernel hence no DMA support.  Everything was slow; the mouse took forever to move across the screen and apps took a long time to load.  Since hdparm hasn't really done too much I'm stumped.  Sorry. :(  The only other thing I can think of is maybe something is using 100% CPU.  During a Synaptic install everything else slows down some on my machine.

---

### Post by Quest-Master on 2005-03-31
I've heard that Linux is supposed to be kept up and running longer, as opposed to Windows slowly deteriorating hour after hour. Only thing I need to figure is how to turn on memory caching for Gnome's main menu..

It's running almost perfect now. :o I think I should try to keep it on longer sometimes. The hdparm DID help, btw. Thanks. :D

---

### Post by bored2k on 2005-03-31
[QUOTE=Quest-Master]I've heard that Linux is supposed to be kept up and running longer, as opposed to Windows slowly deteriorating hour after hour. Only thing I need to figure is how to turn on memory caching for Gnome's main menu..

It's running almost perfect now. :o I think I should try to keep it on longer sometimes. The hdparm DID help, btw. Thanks. :D[/QUOTE]
 If that is true my *machina* should just crash because it doesn't get more than 20hrs uptime, and that's my max. time. I halt -h now every 6-8 hours or so [not because I want do, but because I always find something to do so].

---

### Post by MaX on 2005-03-31
[QUOTE=Quest-Master]... I have no clue frankly what hdc is, hehe. I've also done another cron prelink, and hdparm.[/QUOTE]

hdc is probably your CD/DVD drive.

---

### Post by mr_ed on 2005-03-31
Thank you!  My install has sped up **dramatically**.  Apps used to take aeons to start.

---

### Post by totalshredder on 2005-04-01
[QUOTE=Quest-Master]I should consider getting some new RAM I guess sometime.[/QUOTE]

You shouldn't need RAM, ram is only nessisary if you like to run many programs at once. I only have 256, and I could get by fine with 128; you just can't have as much open :)

About firefox; it's terrible; extremely slow. I switched over to mozilla as soon as I realised how quick it could be. It's amazing how slow it is though, as when I used windows, it took less than 3 seconds to load firefox, and now it takes at least 15 (I know it has something to do with linux compiling it when it starts)

Luke

---

### Post by wmcbrine on 2005-04-02
Quest-Master: Turn on multcount as well as DMA. (Although my system didn't seem slow before I turned on multcount, *except* when trying to play high-def video.)

totalshredder: "...linux compiling it when it starts"? Uh, no, it does no such thing. BTW, my FF starts up in no time. But I wouldn't measure how fast it is by that, anyway, since it's a one-time event; speed while browsing is what counts.

More RAM *does* help, no matter how few apps you run, because Linux uses all spare RAM as disk cache.

---

### Post by maqi on 2005-04-03
[QUOTE=wmcbrine]More RAM *does* help, no matter how few apps you run, because Linux uses all spare RAM as disk cache.[/QUOTE]

WORD UP!!!  8) 

There is no such thing as too much RAM. The more the merrier. And it costs bugger all these days ... so stop being cheap, there's just no excuse  =; 

But seriously ... More RAM will help. And no matter what anyone says, whether you're running linux or Micro$hit, 256MB just doesn't cut it anymore if you want a [color=#CC0000]flashy[/color] desktop.  

Unless, of course, you go to something like Xfce or IceWM, etc.  :) 

maqi

---

### Post by xander on 2005-04-03
What do U think about "hdparm -W1" option?

Should I enable it to increase performance?

X.

---

### Post by neighborlee on 2005-04-05
> **maqi]WORD UP!!!  8) 

There is no such thing as too much RAM. The more the merrier. And it costs bugger all these days ... so stop being cheap, there's just no excuse  = said:**
> flashy[/color] desktop.  

Unless, of course, you go to something like Xfce or IceWM, etc.  :) 

maqi
---------------
more ram wont help that MUCH..I have a P IV 2.26 ghz with 1 gig of rambus and a geforce 4TI4200..and while apps start reasonably fast ( I have dma enbled but not caching ) the gnome menu DOES take eons to draw across the screen compared to kde..so it IS a gnome issue..I wish they would fix it ;-))

OR its the nvidia drivers...if not well its something in gnome...

I love gnome regardless but I hope they resolve this stupid political crap with not taking user input...and gnome guys...NEXT TIME you take away menu editing without asking first..DON'T BOTHER ;-) ( and that weird nautilus decision )

cheers
nl
-------

---

### Post by bored2k on 2005-04-05
[QUOTE=neighborlee]
I love gnome regardless but I hope they resolve this stupid political crap with not taking user input...and gnome guys...NEXT TIME you take away menu editing without asking first..DON'T BOTHER ;-) ( and that weird nautilus decision )
[/QUOTE]

Yes that was suprisingly annoying.. it even made me try kubuntu (of course I went back btw).

---

### Post by nilsmagnus on 2005-04-07
[QUOTE=Nis]
```

/dev/hda {
        mult_sect_io = 16
        io32_support = 1
        dma = on
        read_ahead_sect = 256
}

```

[/QUOTE]
Thanks dude. This speeded up my gnome and firefox loading a lot!

---

