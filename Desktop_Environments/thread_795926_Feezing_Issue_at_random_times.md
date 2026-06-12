---
title: "Feezing Issue at random times"
date: 2008-05-15
forum: Desktop Environments
---

### Post by WarringAngel on 2008-05-15
Ubuntu 8.4 LTS 64bit, becoming very very annoying and I dont want to go back to xp!! At random stages the os will just freeze with no errors in the logs, could be doing anything from idling to playing avi's or just surfing the net, or even downloading torrents. No keys or mouse and the only fix is to do a hard restart.

The beta worked a treat both at home and work, now work has the upgraded version from beta and home has the full lts. Now work is fine all day every day but home is driving me nuts.  The PC is
AMD quad 2.2 gig
Asus ms2 deluxe sli
2gig Match paired DDR800
GT 8800 512mb
sata combo drive
sata 320 gig
ide 80gig

I have tried googling with no luck, also tried sudo apt-get update and
dmesg

Sorry if this has been asked before but I cant find any answers

---

### Post by frogeye on 2008-05-16
seem to have the same issue - i simply loose the ability to control the cursor.  i can access a file via samba from the windows computer, so the computer is sitll running, it is just that i cant do anything on this screen

this is also 8.04 lts amd64

---

### Post by Zoja on 2008-05-16
Yup , me too , the same problem , and i also have AMD64 .. seen a couple of threads on this forum about this problem and none had the answer :/

---

### Post by WarringAngel on 2008-05-16
mmmm not cool, I hate windows but I may have to go back to it and run vmware from it bah hope someone can come up with a fix soon!!!!

Cheers for the comments guys

If anyone has some ideas I am open to try them

I might try turning virtualization off in the bios...

---

### Post by mbhoby on 2008-05-16
Yeah I'm having exactly the same problem, 
AMD64 3200,
2GB Ram,
Nvidia 8600
120GB SATA with OS
250GB SATA

Problem seems to be something to do with graphics, particularly overlays and the like. Any flash intensive website will trigger it as will playing .avi's. Hardware testing does not display graphics overlays at all (colour bars nor static).

As with OP no errors logged and I've updated everything I can think of. On the verge of scrapping the install and putting Gutsy back on...

---

### Post by The Minder on 2008-05-16
Guys,

I'm not sure if I'm close, but I had similar probs on 32 bit 8.04 combined with an nVidia graphics card.   My assessment is that any nVidia driver other than the one that comes with Ubuntu has the potential to cause these freezes.   In short, stay away from restricted drivers, Envy or manually applying drivers from the nVdidia web site.   Once I went right back to basics, the freezes stopped.

Regards

---

### Post by WarringAngel on 2008-05-18
tried that too... I seem to get more issues when closing applications of any sort, just as the close goes though system just freezes, no mouse no keyboard and the total system is non responsive downloads stop hhd transfers stop too.  This appears to be a major bug!!!

---

### Post by ConstantC on 2008-05-18
Freezes here too. Appears really random to me. Can only shut off or reset.
The more applications running, the sooner it freezes.

AMD64 3500, 3Gb,
Ati(!) 9600 graphic
160GbSATA
Dual boot with XP.

---

### Post by WarringAngel on 2008-05-18
going to try and re format swap space, also will watch ram usage / try to find memory leaks.

---

### Post by RAOF on 2008-05-18
There are probably a couple of issues here:
[list]
[*]There was/is a bug in Compiz where the 'animation' plugin could hit an infinite loop, causing X to become unresponsive.  That's been fixed upstream, and there are or soon will be packages in hardy-updates with that fix applied.
[*]There's a fairly long standing nVidia bug which can cause X to lock up when running an OpenGL app (like Compiz) on a multi-processor system (like almost every modern system - dual core counts).  This is not yet fixed as far as I'm aware, although it may be related to...
[*]The obnoxious occasional whole-screen black 'blinks' while running Compiz, which seem to be a result of the video card throttling down when idle.  For both these symptoms, you should see a line with **Xid** in it somewhere in your syslog.
[/list]

---

### Post by WarringAngel on 2008-05-18
ill will have another look at the logs for that line. I have never had any other problems with nvidia and ubuntu before with older versions but was only running a 32bit processor.

---

### Post by WarringAngel on 2008-05-21
now gnome desktop restarting as well. Just sends me to a black screen then back to the log in.

---

### Post by Zoja on 2008-05-27
I've seen that everybody has AMD64 + Nvidia + Ubuntu 8.04 x64 version ... i am trying the i386 version now , and it's 2 days without a hangup

---

### Post by crunchcrunch on 2008-05-29
I'm having the same problem.  My system randomly freezes and the only remedy is to power cycle it.

Ubuntu 8.04LTS
AMD 5400 64bit
Gigabyte ga-ma69gm-s2h
AMD 690G chipset
ATI Radeon X1250-based graphics
Western Digital 160GB SATA HDD

This is my first go at Ubuntu and I really don't want to go back to XP, but I need my system to be reliable.

Any help is greatly appreciated.

Thanks

---

### Post by BuntuFreak on 2008-08-02
Just wanted to let everyone know that this problem is definitely nothing to do with simply AMD or 64 bit. I have Intel 32 and I'm having same problem(s). The only common thing is NVidia.

Then again, I think sticking with Gutsy instead of Hardy was probably the smart thing to do just like sticking with XP instead of Vista.

If an OS cannot upgrade itself what can?

---

