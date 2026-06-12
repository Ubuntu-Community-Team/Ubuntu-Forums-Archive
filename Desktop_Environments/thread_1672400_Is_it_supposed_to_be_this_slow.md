---
title: "Is it supposed to be this slow?"
date: 2011-01-20
forum: Desktop Environments
---

### Post by Scientifik01 on 2011-01-20
I have a fresh install of Ubuntu 10.10 on an old Pentium III Dell. Yes its a dinosaur but wow Ubuntu is running slow. On a fresh boot up and looking at the system monitor, its using about 477mb of 496mb available RAM, 100% of the 1.5 gig swap and the CPU is averaging about 22%. I get this isn't the fastest machine in the world but I can't even move the mouse around the desktop without major lag. Is there something I'm doing wrong, is there a way to run this in a lower resource mode and free up some memory and the swap file?

---

### Post by ronnielsen1 on 2011-01-20
You don't say how fast of a P3 it is, but with less than 512 M of ram, yes, Ubuntu would be slooooowww. Your best bet would be either install a lighter weight window manager like lxde, fluxbox or openbox or try an alternative distro like antiX, lubuntu, puppy

[http://book.opensourceproject.org.cn/distrib/ubuntu/hacks/opensource/0596527209/i-0596527209-chp-2-sect-3.html](http://book.opensourceproject.org.cn/distrib/ubuntu/hacks/opensource/0596527209/i-0596527209-chp-2-sect-3.html)

> GNOME and KDE are great, but they are a little heavy. If you're on an older system, or you just want a change of pace, you can use other window managers under Ubuntu, such as Fluxbox, XFCE, and Enlightenment.

One I reccomend for older boxes
[http://antix.mepis.org/index.php?title=Main_Page](http://antix.mepis.org/index.php?title=Main_Page)

---

### Post by mikewhatever on 2011-01-20
Scientifik01, can you show us the output of the **free -m** command. Obviously it shouldn't use so much memory and swap.

---

### Post by Krytarik on 2011-01-21
RAM usage is normal, mine is currently running at 534 MB, with Firefox, Thunderbird and a Last.fm client running. CPU usage is also normal given the fact that the System Monitor itself utilizes the CPU considerably. But Swap usage is far to high even with RAM maxed out. That would explain the lagging mouse. What video card/chip have you installed, maybe even an onboard chip with shared memory?

---

### Post by Scientifik01 on 2011-01-27
Ok sorry for the late response, I forgot to enable auto subscriptions and notifications. I ordered some more memory and that should be here shortly. Once I try the ram upgrade I'll probably switch to a different window system, since this is mostly a file server. However a different problem would be the swap seems t be maxing out. I just booted it up and ran free -m and this is what I get
                  Total        Used       Free
Swap:         1497       1497          0

This is a pretty fresh install of 10.10 just after startup. Any thoughts?

---

### Post by Krytarik on 2011-01-27
I honestly don't have an idea why your swap usage is that high.

Try running a LiveCD, both 10.04 and 10.10.

I hope you don't have the 64bit installed?! I don't know if it will get installed if you don't have a 64bit CPU.
Run "uname -r" to check it.

Btw., how fast is your CPU (Mhz)?

Regarding the desktop environment, look here for more info to make a proper choice (don't mind the topic):
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by Bucky Ball on 2011-01-27
You could try installing Xfce:

[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

---

### Post by Scientifik01 on 2011-01-27
The Dell service tag shows that its a 1.7gHz. 

I think maybe a major problem is the swap file, if its maxing out how  can I either a) allocate more memory to it or b) bring it down to a more  normal level.

As it is right now I don't think I can even install a replacement desktop, its taking me 30 seconds just to SSH.

---

### Post by Krytarik on 2011-01-27
> **Scientifik01 said:**
> The Dell service tag shows that its a 1.7gHz. 

I think maybe a major problem is the swap file, if its maxing out how  can I either a) allocate more memory to it or b) bring it down to a more  normal level.

As it is right now I don't think I can even install a replacement desktop, its taking me 30 seconds just to SSH.
Check if this guide helps you:
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by Maximus559 on 2011-01-28
That is an odd problem. I hardly ever see Ubuntu utilize over 300 MB of RAM. When I only had 512 MB RAM installed, my 1.8 GHz P4 Dell ran just fine. You might give Xubuntu a shot, and if that's still not light enough, try [SliTaz]("http://www.slitaz.org/en/"). It's lighter than anything that's been suggested so far, and it should absolutely fly on your machine. If it doesn't, there's something else going on.

---

### Post by Timmer1240 on 2011-01-28
> **ronnielsen1 said:**
> You don't say how fast of a P3 it is, but with less than 512 M of ram, yes, Ubuntu would be slooooowww. Your best bet would be either install a lighter weight window manager like lxde, fluxbox or openbox or try an alternative distro like antiX, lubuntu, puppy

[http://book.opensourceproject.org.cn/distrib/ubuntu/hacks/opensource/0596527209/i-0596527209-chp-2-sect-3.html](http://book.opensourceproject.org.cn/distrib/ubuntu/hacks/opensource/0596527209/i-0596527209-chp-2-sect-3.html)



One I reccomend for older boxes
[http://antix.mepis.org/index.php?title=Main_Page](http://antix.mepis.org/index.php?title=Main_Page)

Thanks I got an old machine down in my basement with Ubuntu and its a little slow Once I get an ethernet cable run down to it Im gonna try Antix on it looks like a great little lightweight distro!

---

### Post by SeijiSensei on 2011-01-28
You could try turning off swap as an experiment.  Just run the command "sudo swapoff".

I, too, have no idea why it would be eating swap like that.  I have some virtual servers with 512M and 256M swap, and they're perfectly happy, though of course, they're not running a GUI desktop environment.  

If your box really is just a server, then try booting into text mode and avoiding the GUI entirely.  See [this post]("http://ubuntuforums.org/showpost.php?p=8800306&postcount=2") for details.  (It references [this blog post in Spanish](http://www.hipergalaxia.org/blog/2010/01/05/iniciar-linux-ubuntu-9-10-en-modo-solo-texto/) which offers another solution as well.)

---

### Post by xiongnu on 2011-01-30
I am running Ubuntu on an old Dell PC (600Mhz) and i also found default GNOME is too slow for me.  so I first tried IceWM and it's a nice improvement, but it's just a bit too simplistic, then i added XFCE as my default desktop environment, which runs pretty well.  

I've since axed GNOME from my linux box and it freed over 1GB hard drive space and it runs faster than before.

---

### Post by Rab22 on 2011-01-30
Yes, I would use a different window manager.

I'd probably install ubuntu netbook if I wanted to keep something close to typical GNOME. It should run better on older hardware.

---

### Post by robert shearer on 2011-01-30
If it is a P3 then I doubt that its 1.7gHz.

How about running...
```
sudo lshw
```
and posting the output here.

lshw=list hardware.

---

### Post by asmoore82 on 2011-01-30
> **Krytarik said:**
> RAM usage is normal, mine is currently running at 534 MB, with Firefox, Thunderbird and a Last.fm client running

Something is odd. 

I have 2 machines both running 10.04 LTS.
My laptop which is a development workstation and
my desktop which is a DVR driving an HDTV.

The laptop has a Core i7 Quad @1.7 GHz and 8GB of RAM.
The desktop has a Sempron 3400 @1000 MHz and 512MB of RAM.

The laptop was using 900MB of RAM so I shutdown
apache2, tomcat, mysql, postgresql, and schooltool...

That brought me down to using about 540 MB of RAM - shockingly close to Krytarik's number.

`top` shows my biggest memory hogs as firefox, xorg, compiz which is as expected.
So now even if I disable all desktop effects, my RAM usage is still up at around 490MB.

Switch gears to, as I call it, "The TV computer."
No desktop effects there, but right this very moment it has Firefox with 5 tabs open
and is playing a live over-the-air 1080i HD stream via mplayer ...
it's using only 275MB of RAM, 50MB of swap.

So what gives? My desktop proves that it must be possible
to run Ubuntu comfortably within only 512MB of RAM.
But neither my laptop, Krytarik's machine, nor the OP's can seem to do it.

---

### Post by Krytarik on 2011-01-30
To get close to the programs running at your "TV computer", I opened 5 tabs in Firefox (with different sites), play a video in smplayer, subtract Thunderbird, Compiz, Pidgin, alarmclock-applet, System Monitor and gcalctool = 414 MB, - 325 MB of your TVC = 89 MB difference.

Though I didn't check how much Metacity uses. And your summary was incl. System Monitor or Terminal? I guess it's in the end a negligible difference, but the question indeed remains: Where are those MBs?;)

---

### Post by Krytarik on 2011-01-30
> **Rab22 said:**
> Yes, I would use a different window manager.

I'd probably install ubuntu netbook if I wanted to keep something close to typical GNOME. It should run better on older hardware.
Unless you can't enable hardware accelerated video; then you would in fact barely see anything at your desktop.;)

---

### Post by cascade9 on 2011-01-30
> **Scientifik01 said:**
> I have a fresh install of Ubuntu 10.10 on an old Pentium III Dell. Yes its a dinosaur but wow Ubuntu is running slow. On a fresh boot up and looking at the system monitor, its using about 477mb of 496mb available RAM, 100% of the 1.5 gig swap and the CPU is averaging about 22%. I get this isn't the fastest machine in the world but I can't even move the mouse around the desktop without major lag. Is there something I'm doing wrong, is there a way to run this in a lower resource mode and free up some memory and the swap file?

Wow, very high swap use, but aside from that, pretty normal. 

There is a reason why the recommended requirements for ubuntu is 1GB now- 

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Ubuntu, and xubuntu and kubuntu for that matter, have never been built for 'lightness'. That doesnt mean that you cant have a much, much less RAM hungry system with ubuntu, and without using the horror that is lubuntu/Lxde. 

Minimal install + Xfce4, or minimal + gnome-core should reduce your boot up RAM requirements to a quater or less than your current 477MB RAM use on boot up. 

You could also just install the Xfce4 base on top of your current ubuntu and reduce the RAM required a huge amount. It wont be as low as a minimal install + Xfce , and possibly not even as 'light' as minimal install + gnome-core, but at least you wonthave to d/l the alternate .iso, reinstall, get all your udates, etc. 

sudo apt-get install xfce4 

Change the desktop you are loging into from 'ubuntu-dekstop' to xfce4 and you should have a far more usable system. You might need to change the GDM login screen to get the option to change DE from what I've seen. 

BTW, just for fun- my KDE 4.4.5 desktop boots with less than 230MB of RAM use. That is running kwin effects, and I havent done any lightening mods to get that figure....

---

### Post by P4man on 2011-01-30
Something is leaking memory BADLY. No matter how slow or fast your cpu, with all your ram and swap used, its gonna be incredibly slow. Just run 

```
ps aux
```

in a terminal and find out which process is eating up your address space.

BTW, with those specs, even with just 512MB, ubuntu should run acceptably if you dont start too many / big apps.

---

### Post by Tasty Bacon Vortex on 2011-01-30
You could give ***[Bodhi Linux]("http://www.bodhilinux.com/")*** a try. It uses 10.04 Lucid and can run on a minimum 300mhz processor and 128mb RAM. The E17 desktop needs a bit of time getting used to to navigate around but definitely looks way better than xfce, lxde, fluxbox, etc.

---

### Post by asmoore82 on 2011-01-30
OK, I turned off all of my server processes and
booted with the param "mem=512M" ...

After logging in, I stopped samba and winbind,
I switched to metacity,
I killed all of these, to simulate the TV Computer:
 1. evolution-* (Evolution backends)
 2. gdu-* (That disk usage notifier)
 3. gnome-power-manager
 4. indicator-message-*
 5. python (The print queue applet)

So I've now got a gnome-terminal, System Monitor and
this Firefox with 7 tabs open,
I'm using 277MB of RAM, 3.2MB of swap.

So you can slim down Ubuntu w/Gnome to be comfortable within 512MB.
All of those that I killed can be turned off nicely and permanently in
"System -> Preferences -> Startup Applications"
Which I'm pretty sure is what I did for the TV computer ages ago.

I would much rather have this slim Gnome that any of those other
"light" suggestions; but that's just me.

P.S. I guess it never hurts to have a cheap, dedicated video card :P.

P.P.S. The attached screenshot is priceless, 8 CPU threads but <500MB RAM :lol:

---

### Post by Scientifik01 on 2011-01-30
Ok so I did a couple things, first off the 1GB of RAM I ordered was bogus and gives a post tone immediately on boot no matter what configuration I put it in, so for now I'm stuck with 512. :mad: 

I was able to boot into text only mode which really is good enough for this machine, I did find the culprit for the swap hogging appears to be [ushare]("http://ushare.geexbox.org/") Doing a simple "service stop" doesn't seem to affect it I have to kill the process and when I do memory and swap go down to much more reasonable levels.

---

### Post by Krytarik on 2011-01-30
How did you find it?
It isn't even installed at my machine.

---

### Post by robert shearer on 2011-01-30
> **Scientifik01 said:**
> Ok so I did a couple things, first off the 1GB of RAM I ordered was bogus and gives a post tone immediately on boot no matter what configuration I put it in, so for now I'm stuck with 512. :mad: 

Before jumping to conclusions, **IF**, as you say, you have a p3 (probably not 1.7gHz) then some of the chipsets that are associated with those only support 512 anyway !. Of course it will beep then as it doesn't support 1Gb.

In a terminal run...
```
sudo lshw
``` 
and paste the output (putting it inside code tags as it is a large output.)
and run and report also..
```
sudo dmidecode
```
Which will tell us how much ram is supported, what the cpu is etc.

---

### Post by Bucky Ball on 2011-01-30
> **Scientifik01 said:**
> Ok so I did a couple things, first off the 1GB of RAM I ordered was bogus and gives a post tone immediately on boot no matter what configuration I put it in, so for now I'm stuck with 512. 

Sometimes the RAM doesn't work first up and can be inserted incorrectly. I know this sounds a little crazy, but get an eraser (a rubber that rubs out pencil) and rub the part of the RAM that inserts into the board. Not to vigorously or hard, naturally.

This can clean away any factory gunk or matter which is preventing the RAM getting a clean contact with your machine. 

If still no go, send it back for a replacement! Lots of RAM has a lifetime warranty and if not it should have some. Don't get ripped off! ;)

*Robert shearer has a point also. It would give a beep if it can't take that much RAM. The other possibility is it might not take that much RAM in *one* slot but may take it in two (512x2 in two separate slots = 1Gb).

---

