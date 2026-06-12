---
title: "ANCIENT LAPTOP--Can Linux Save it?"
date: 2009-05-25
forum: General Help
---

### Post by ShinHadoken on 2009-05-25
I found an absolutely ancient old Dell Latitude laptop. Can't remember what processor off the top of my head, but it only has 8MB of RAM and a 100MB hard drive. My only optical drive is a 3 1/2" floppy drive. What Linux distribution would be best equipped to revive this old clunker? I'm not looking to actually use it for anything, of course. Just a fun little project, thought I might see just how much I could get this thing to do. So, suggestions?

Thanks!

James

---

### Post by ShinHadoken on 2009-05-25
bump

---

### Post by piousp on 2009-05-25
Try damn small linux

---

### Post by snowpine on 2009-05-25
Computer museum?
Not worth the cost of electricity to keep it running in my opinion.

---

### Post by jmszr on 2009-05-25
ShinHadoken,

        Here is a link to a list of small distros: [http://www.linuxlinks.com/Distributions/Mini_Distributions/](http://www.linuxlinks.com/Distributions/Mini_Distributions/) . It looks like Tiny Linux would fit your specs: [http://tiny.seul.org/en/](http://tiny.seul.org/en/) .

---

### Post by ShinHadoken on 2009-05-25
That's good, but my only problem is getting it on there. It only has a floppy drive, and all of my floppies are 1.38 MB, not enough to fit even the smallest distribution on that list, which is 3.1 MB. I haven't shopped for floppies in so long--can you order some that are bigger?

---

### Post by dandnsmith on 2009-05-25
With 100MB HDD, and 8MB RAM, it's going to have to be something with a CLI rather than a GUI (my guess).

Try [toms root n boot](http://www.toms.net/rb/) which can be fitted onto a floppy. From memory you need to have it in a higher density mode for the floppy, and not all floppy drives can support this  worth a try tho'

---

### Post by jmszr on 2009-05-25
ShinHadoken,

According to the Tiny Linux installation instructions, one needs 14 1.44 MB (1.38MB?) floppies for installation: [http://tiny.seul.org/en/i.html](http://tiny.seul.org/en/i.html) .

---

### Post by ShinHadoken on 2009-05-25
dandnsmith: It's got Windows 98 on it currently, so it's capable of running a GUI. Just gotta find a way to get everything on there, that's the problem.

jmszr: 14 1.44MB floppies, eh? Well, I don't know if I have that many, but I can dig around and see.

---

### Post by ShinHadoken on 2009-05-25
Looks like I don't, but I can probably find some somewhere... Floppies aren't THAT old, are they?

---

### Post by jmszr on 2009-05-25
ShinHadoken,

In technological time they are. Nevertheless, here are some for sale:[http://www.sjgreatdeals.com/mxlmf2hd10pk.html](http://www.sjgreatdeals.com/mxlmf2hd10pk.html). I'd like to know how your project turns out.

---

### Post by ShinHadoken on 2009-05-28
Well, I'll order some floppies. In the meantime, I'm going to explore option number two, installing DSL (Damn Small Linux). In order to do this, I would need a boot floppy such as Tomsrtbt or BGRescue Linux, but I can't get either of those to work (can't figure out how to make a toms disk, and BGRescue complains of not finding a valid initd image) Does anyone know of a Linux boot floppy such as those, other than those?

---

### Post by ugm6hr on 2009-05-28
I think 16MB is a bare minimum for DSL; good luck trying!

I have heard GreyCat & BasiclINUX will run on 8MB (never tried): [http://www.angelfire.com/anime/db/gcl/](http://www.angelfire.com/anime/db/gcl/)
[http://distro.ibiblio.org/pub/linux/distributions/baslinux/](http://distro.ibiblio.org/pub/linux/distributions/baslinux/)

A non-Linux distro like Kolibrios might work too (although less hardware support): [http://www.kolibrios.org/](http://www.kolibrios.org/)

And I just stumbled across an actively developed tiny Linux (CLI only): [http://minimalinux.org/ttylinux/](http://minimalinux.org/ttylinux/)

The other option is to track down an old 2.4kernel distro, or try an older BSD release.

However, I think you will not get much done with it!

---

### Post by ShinHadoken on 2009-05-28
Well, I've exhausted all of those options, none of the floppies will a) boot or b) give me a system that's workable with. So, I'm left with trying to track down an older version of a distro. I know it's not impossible guys, it's got Windows 98 on it and it runs fine. Surely there's a Linux out there that can run with 8MB of RAM, 100MB hard disk space, and installs by floppy, even with the help of a network card? What about an older version running 2.4x or even 2.2x kernels, does anyone know of any?

---

### Post by albinootje on 2009-05-28
> **ShinHadoken said:**
> I found an absolutely ancient old Dell Latitude laptop. Can't remember what processor off the top of my head, but it only has 8MB of RAM and a 100MB hard drive. 


There was a similar thread about this a few months ago here. Your best bet imho is an old Debian or Slackware version.
Slackware was actually a well-known Linux distribution around 1995 which still offered a full installation with floppies for quite some time.
I once did an install based on floppies, I used one machine to create the first 3 floppies, after using them I recreate the next 3 floppies on another machine, etc.etc.

I think Slackware 3.x would be a good choice, and Debian Potato.

Slackware had documentation included for people wanting to install on 8 Mb RAM machines.

You should also realise that you're going back more than 10 years, don't expect a fast shiny desktop at all, go for the CLI, and just playing around. With 8 Mb of RAM you might even have to go further back, or give up and try something else than Linux on it, FreeDOS for example.

---

### Post by albinootje on 2009-05-28
> **ShinHadoken said:**
> I know it's not impossible guys, it's got Windows 98 on it and it runs fine. 

That doesn't mean that Linux will run on it fine.
Try the Qnx demo, perhaps Minix will run, just do some more research.
> 
Surely there's a Linux out there that can run with 8MB of RAM, 100MB hard disk space, and installs by floppy, even with the help of a network card? What about an older version running 2.4x or even 2.2x kernels, does anyone know of any?
Sorry for not reading the whole thread completely, see my previous comment. 

Good luck, .. but have fun! :-)

---

### Post by ShinHadoken on 2009-05-28
> **albinootje said:**
> You should also realise that you're going back more than 10 years, don't expect a fast shiny desktop at all, go for the CLI, and just playing around. With 8 Mb of RAM you might even have to go further back, or give up and try something else than Linux on it, FreeDOS for example.

Hehe, oh I realize that. Yea, it's definitely just a toy, and I want to install just whatever will run on it, whether it's CLI or an all-out X-session. Thanks, I'll dig around and look for a Debian/Slackware boot floppy and give it a shot.

---

### Post by ShinHadoken on 2009-05-28
Well, I dug around on the web and I can't find anywhere to download Debian or Slackware (the older versions) so I emailed people with each organization asking for a floppy image. In the meantime, if any of you guys can find an image on the net, let me know!

---

### Post by ugm6hr on 2009-05-28
> **ShinHadoken said:**
> What about an older version running 2.4x or even 2.2x kernels, does anyone know of any?

DSL actually still uses the 2.4 kernel.

How far did you get with it?

If you want X running, it probably remains your best bet for a modern solution...

PS: Archived versions of DSL since 2003 remain available on their mirrors.

---

### Post by albinootje on 2009-05-28
> **ShinHadoken said:**
> I can't find anywhere to download Debian or Slackware (the older versions) 

Here you are :
[http://archive.debian.org/debian-archive/debian/](http://archive.debian.org/debian-archive/debian/)

Try these, to start with :
[http://archive.debian.org/debian-archive/debian/dists/Debian-2.2/main/disks-i386/2.2.26-2001-06-14/images-1.44/](http://archive.debian.org/debian-archive/debian/dists/Debian-2.2/main/disks-i386/2.2.26-2001-06-14/images-1.44/)

Afair, the rescue.bin is the first install floppy you need.
And read this : [http://archive.debian.org/debian-archive/debian/dists/Debian-2.2/main/disks-i386/2.2.26-2001-06-14/README.txt](http://archive.debian.org/debian-archive/debian/dists/Debian-2.2/main/disks-i386/2.2.26-2001-06-14/README.txt)

---

### Post by albinootje on 2009-05-28
Perhaps you can even test it first on another machine with VirtualBox, by giving the guest VM only 8 Mb of RAM.
But I don't remember how you would switch floppies in VB.. I think I read it was possible.

---

### Post by ShinHadoken on 2009-05-28
ugm6hr: I'd love to do a Poorman's install of DSL (simply downloading the iso image to the hard drive, via a boot floppy, and booting from that) but I can't find a boot floppy that will allow me to fdisk and wget. All the floppies out there either won't boot on my low specs, or give me a BusyBox term, which is useless. If I could find a good boot floppy, this would be the first strategy I'd try.

albinootje: Thank for those links! I'll check them out right now...

---

### Post by ShinHadoken on 2009-05-28
That's what I've been doing, testing them all on Vbox... can't change floppies? Maybe that's why they haven't been working... =|

---

### Post by Steelmourne on 2009-05-28
8MB RAM? Give up. Mozilla takes up 23mb at start-up. Even lighter apps will strangle it.

---

### Post by ShinHadoken on 2009-05-28
> **albinootje said:**
> Here you are :
[http://archive.debian.org/debian-archive/debian/](http://archive.debian.org/debian-archive/debian/)

Try these, to start with :
[http://archive.debian.org/debian-archive/debian/dists/Debian-2.2/main/disks-i386/2.2.26-2001-06-14/images-1.44/](http://archive.debian.org/debian-archive/debian/dists/Debian-2.2/main/disks-i386/2.2.26-2001-06-14/images-1.44/)

Afair, the rescue.bin is the first install floppy you need.
And read this : [http://archive.debian.org/debian-archive/debian/dists/Debian-2.2/main/disks-i386/2.2.26-2001-06-14/README.txt](http://archive.debian.org/debian-archive/debian/dists/Debian-2.2/main/disks-i386/2.2.26-2001-06-14/README.txt)

So, I'm gonna need 17 floppies?

---

### Post by marshag63 on 2009-06-01
Hello!  How about a Debian net install - takes four disks.  If you have a live cd you can boot in another machine, you can download the info for the four disks and then burn them to floppy.  

[http://www.debian.org/distrib/netinst#verysmall](http://www.debian.org/distrib/netinst#verysmall)

Choose the floppy images.  You don't want network boot, you want network install.  Make sure you make a swap partition (two to three times RAM).  Go for a CLI install - you will be amazed what you can do.  

CLI apps I recommend :  
elinks - g (graphical mode)
screen - cli window manager thing
irssi - cli IRC client
mutt or elmo - mail client
moc = music player (with ffmpeg if you plan on playing your MP3s)
mplayer (no gui version) if you can use framebuffer.  If that works, you can download youtube vids with clive.
nano and vim - text editors.
top - system monitor

I once managed to get Damn Small Linux on an old Compaq with 16 mb ram - the key is the swap partition, and the fact that it had a CD-rom.

I've installed Debian twice via network install on machines whose CD drives no longer worked and were unable to boot from USB.

Good luck and let us know how it goes.

MarshaG.

---

### Post by ShinHadoken on 2009-06-01
Update on my project: Got Debian Slink installed (boy, did THAT bring back some memories!) and now all I have, essentially, is dselect. Because I don't have an NIC, my only option is to write everything I want to install to floppies and install it all that way. Also, when I went to format the hard drive, discovered that I actually have a 250MB hard disk! (instead of 100MB if you haven't been following this) If I give Debian a 50M swap partition, could I get away with installing 2.2 ([Potato]("http://www.debian.org/releases/2.2/i386/ch-hardware-req.en.html#s2.3"), CLI install of course) Anyway, whether or not I install Potato, I still need to know: which packages do I install (just want a basic toolbox) where do I get them, and how exactly do I write them to the floppies? (Do I/How do I make a "Packages" file, and do I write them to the floppies, or just copy the .deb's over?) Because am starting from scratch and reinstalling with Potato, I'll wait for an answer here before I take any further action.

---

### Post by Harpie Queen on 2009-06-01
Floppies aren't that old, I remember using them and I'm still in school. I still have some lieing around, and soon I will have a floppy drive in my new computer, because nostalgia for my childhood demands it. I also have a few floppies lieing around. I guess if you can't dig any up go to lots of computer stores, or use ebay. They will be somewhere.

---

### Post by ShinHadoken on 2009-06-02
I've got some, found about thirty of them lying around. I'm set on floppies. What I need to know is can I install Potato, and how do I get packages on there with floppies.

---

### Post by ShinHadoken on 2009-06-03
Bump please

---

### Post by ShinHadoken on 2009-06-04
bump

---

### Post by crazypeppo on 2009-06-04
+for DSL attempts
check out: [http://distrowatch.com]("http://distrowatch.com")

maybe try puppylinux?

If you laptop has windows on it are you just trying to play with linux?
You can use apps from: [http://portableapps.com]("http://portableapps.com") to get the feel...

also check out: [http://pendrivelinux.com]("http://pendrivelinux.com") I know they install them on USB Drives but see what some of the guys have stripped down... 

Good luck & keep us posted...

Here's another one I remembered:
[http://www.linuxlinks.com/Distributions/Floppy/]("http://www.linuxlinks.com/Distributions/Floppy/")
Look for Floppix

---

### Post by mixmaster on 2009-06-04
I remember installing an early slackware from floppy onto an IBM PS/2 model 80, which I'm sure had a lower spec than your laptop.  This would have been in the mid 90's so I would guess it was slackware 2.x or 3.0.  For a long time the floppy set sat in the back of a cupboard at work (I am something of a pack-rat) but I think I dumped it comparatively recently.  If I didn't I'll see if I can dig it out.

I've no idea what use the thing will be without some form of network connectivity though.  I was using it to drive a large (for the time) screen thus converting the old ps/2 into a high-function xstation using a token-ring network, although I'm pretty sure the distro supported ethernet - at least the co-axial CSMA/CD version.

I think I'll go and lie down.  This reply is making me feel very old.

---

### Post by andyprough on 2009-06-04
> **ShinHadoken said:**
> I've got some, found about thirty of them lying around. I'm set on floppies. What I need to know is can I install Potato, and how do I get packages on there with floppies.

Might try MuLinux first - can install the whole thing on one floppy (save you a bunch of floppies!),  and it has some add-ons you can install with additional floppies. Looks like a lot of fun actually!

Says it can be installed from Win98 without repartitioning:
[http://mulinux.sunsite.dk/download.html](http://mulinux.sunsite.dk/download.html)

The distro is old and no longer under development, but it could be fun to play around with.

---

### Post by marshag63 on 2009-06-04
BasicLinux

Two floppies, plus X - - try BL1  as it is for 8 MB.

[http://www.basiclinux.com.ru/](http://www.basiclinux.com.ru/)

I would also recommend a serial to USB cable or a PCMCIA modem or network card.

MarshaG.

---

### Post by pawnrocket on 2009-06-04
Does this latitude have Network boot? 

I have a Latitude CPi ... That damn thing flies with pup 4 on it. I also connect to the LTSP server again, it screems. I like the LTSP option better really, I can still have a killer desktop (ubuntu) without having to worry about the hardware dying on it. If it fails I can just find another old useless laptop and connect via network boot and still have everything. 

I love TS technology.

---

