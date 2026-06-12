---
title: "Slimming down XUBUNTU even more"
date: 2006-08-26
forum: Desktop Environments
---

### Post by ashrack on 2006-08-26
On this old PC
Pentium II 350@390 MHz
196MB SDRAM
40GB IBM 7200RPM HDD with DMA ON

On it I have XUBUNTU installed! And I already removed lots of crap with the help of DEBFOSTER and also removed some deamons thru SYSV-RC-CONF program! 
But it trashing a lot to swap file with only FIREFOX open.
THe top command output that there is 3MB of RAM free and around 70MB of swap file used.

IS there a way to even further slim down the RAM usage?

---

### Post by backdoc on 2006-08-26
I think a better approach would be to start minimal and build up (as opposed to starting with a complete system and trimming).  While XFCE4 is a light weight, full featured desktop, it's not the lightest.  I don't know what gets installed when you choose the Ubuntu server install.  I've never compared it to any other distro.  But, if it were me, I would consider going with another distro like slackware, damn small linux, arch or plain old debian.  It will be considerably more difficult to get the system up to the way you want it, but considering you are trying to install Linux on antiquated software, I think that is the trade-off you will have to make.  In the long run, you will benefit from the learning.

I'm not trying to discourage you using *buntu.  But, for what you are trying to accomplish, I'm not sure it is your best choice.  For the record, on modern hardware, I think *buntu rocks.

---

### Post by lagagnon on 2006-08-26
You are pushing the limit of useability with only 196MB of RAM trying to run X under xfce and Firefox on a Ubuntu system. For a more useable system I would recommend adding a 256MB stick of RAM to that baby (they are very cheap nowadays) or else using an even lighterweight distro as the previous poster mentioned. But I would add two other distros to consider:

VectorLinux or PuppyLinux.

Have fun.

---

### Post by kerry_s on 2006-08-26
You can do a server install + fluxbox to get the fastest system for that computer. Just grab a copy of the latest ubuntu dapper alternate cd ( [http://ubuntu-releases.cs.umn.edu//6.06/ubuntu-6.06.1-alternate-i386.iso](http://ubuntu-releases.cs.umn.edu//6.06/ubuntu-6.06.1-alternate-i386.iso) ) and select server install, that will give you a barebones system with no gui.
after you sighn in with the user you created, do> sudo su <that makes you root, then do > nano /etc/apt/sources.list < nedd to edit > comment(#) out the cdrom repo and uncomment(#) all the other repos , then press> ctrl + x <then> y <then> enter < to save it. Now do> apt-get update <and then> apt-get install fluxbox x-window-system-core xdm xterm <this give's you fluxbox and a terminal, now type reboot and you should now come up to a gui login, login and opea the terminal(right click) now you can start apt-getting what ever you want, I usally go gui from here on so i do> sudo apt-get install synaptic < type> sudo synaptic & < to launch it. Thats the basics for installing fluxbox, after that it's all a matter of setting it up and picking the apps you want to use and getting a decent look you can live with. Here's a pic of mine->

---

### Post by kaamos on 2006-08-26
Don't use a login manager.

I have a fujitsu lifebook with 500mhz cpu and 128mb ram. It is quite fast with server install + xfce (not xubuntu-desktop, just the minimal setup). Just starting from the cli instead of using gdm or wdm makes the system a whole a lot faster to boot.

---

### Post by lavinog on 2006-08-26
I'm running Xubuntu on an Dell cpi D300XT laptop: 300mhz P2 with a 6g hd, 128meg ram (additional memory would cost more than a new laptop. 128meg module runs about $300!)
In many cases it seems faster than win98se on the other partition.
The only issues that I have still to work out is the soundcard doesn't work (thats why i have win98 on here still,) and it looks like the fan doesn't turn on (but this laptop seems to stay pretty cool on its own)
I use firefox, sometimes I can have up to 20 tabs with no big delays. As far as memory with firefox running: memory usage is about 74MB out of 123MB and swap is 18MB out of 125MB.
I installed it with the alternate install disk.
and only run 2 workspaces instead of the default 4.

I run a cpu, mem graph on the task bar. Occasionally the cpu maxes out, but yet the system is still responsive. (which cannot be said for windows)
As for windows xp. I tried it on this machine, about the only thing you can do is explore the drives without the swap file going nuts.
BTW: I have a microsoft wireless card ($5 clearance) that doesn't  work with win98se or xp, But xubuntu worked with it right away. go figure?

---

### Post by secdroid on 2006-08-26
I concur with kerry_s about the server install and fluxbox.  I've been playing with all of the alternatives this weekend, trying to decide whether it is worth my while to buy an older laptop.

Doing a server install and then adding the XFCE bits one-by-one is hugely difficult.  On the other hand, Xubuntu is not that lightweight.  (Very nice, but not that light.)

I did do the server install and fluxbox.  Fairly easy to do and the result was quite acceptable.  Of course, I'm used to Damn Small Linux (DSL), another fluxbox linux.

FWIW, I've concluded that 300-400 MHz, 128-256 MB laptops work best with really light linuxes like DSL or Ubuntu Server with fluxbox.  Xubuntu works best with just a bit more resources.  

It may not be cost-effective to upgrade a laptop like yours to run Xubuntu, unless you have access to free parts.

You might want to check out other lightweight distros at [http://distrowatch.com/]("http://distrowatch.com/")

YMMV

---

