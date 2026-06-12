---
title: "best distro for an old dell?"
date: 2007-06-02
forum: Dell  Ubuntu Support
---

### Post by iamdigitalman on 2007-06-02
Ok, sorry if this is in the wrong place, but is it not a forum to ask questions about ubuntu on dells?

anyways,there is this old family Dell Optiplex GXM 5166, and I have had it run a multitude of windows versions. 2000, ME, 98SE, and it originally came with 95. I did a clean install of 98SE, and with the virus scanner and office suite, it is acting very bogged down. Firefox is also acting wierd, crashing 2 or 3 times an HOUR!! So, getting sick of all the viruses and other crud, I figured I will try Ubuntu on this old beast.

It has very tiny specs, and I don't know if xubuntu will play comfortably. here are the specs:

pentium I 166mhz
64mb (4x16mb) RAM
2gb HD
3 ISA, 2 PCI/IDE combo expansion connectors
floppy
CD-ROM
USB 1.1 PCI card
SMC 10/100mbps LAN card
S3 Trio 64v+ (or something like that) video, 1mb of VRAM built in
2 serial ports built in
1 parallel port
built in soundblaster
2 PS/2 ports
built in 10mbps RJ-45/LAN jack

so yeah, not the best specs, but all it will do is browse the web, check email, and write papers and such. 

I want to try fluxbuntu, but I don't know if it's finished, and I don't want to run beta software, and I don't know if it is an offical version of the ubuntu project.

any thoughts?

-digital ;)

---

### Post by crispy_420 on 2007-06-02
I think minimum specs on Xubuntu are 128MB DDR. I have a similar model myself and I tried many different versions of linux before I found one that worked. After many so-called low spec distros (I tried about a dozen), I ended up installing Damn Small Linux. The install will only consume about 50MB and you'll have the rest to play with. You can add more apps as needed like email and office/writers. Look here for a how to: [http://www.damnsmalllinux.org/wiki/index.php/Installing_to_the_Hard_Disk](http://www.damnsmalllinux.org/wiki/index.php/Installing_to_the_Hard_Disk)

---

### Post by iamdigitalman on 2007-06-02
actually, xubuntu will work with 64mb with the alternate CD, but I doubt it will work well.

yeah, I have tried DSL before, but only the embedded flavor that runs inside of windows. it's really nice. never knew you could use it as your primary OS, or even expand it. i'll have to give it a try. If I remember the specs, that runs on as low as 16mb and a 486!!

one of my major concerns is speed. I know I will never be able to win any races, but I would at least like it to boot in less than 5 minutes, and not crash all the time.

there is one samll detail I left out: there is a HP jornada 520 series hooked up to one of the serial ports. We used to sync it on another machine running XP, but that one died. then when I tried it on the dell with ActiveSync 3.8, it did not work on either serial port. is there something like that for linux?

-digital ;)

---

### Post by jgrabham on 2007-06-03
Puppy, although it feels like win95 with lots of strange apps :]

---

### Post by octathlon on 2007-06-03
I suggest going to [www.distrowatch.com](www.distrowatch.com) and checking out the pages for DeLi, Puppy, Damn Small, BeaFanatIX, and Austrumi.  There will be links to reviews, and this last week's Distrowatch had a good review of DeLi linux you should read.

Firefox and other big apps like Open Office are not going to work on such an old system though.  Fortunately there are plenty of alternatives.

---

### Post by iamdigitalman on 2007-06-03
well, I really want something ubuntu or at least debian based, as that is the flavor I have the most experience with, and would be able to help my parents with the most.

so, I looked around, and I came across [This]("https://help.ubuntu.com/community/InstallingUbuntuLite"), and it seems like a viable alternitive. However, the instructions there are for breezy, the version I got my start in. Would the same instructions hold true for 7.04? It seems like a viable flavor.

Also, I won't have the chance to work on this for a few days, until I get the power supply for my new monitor on my mac, since I am borrowing the CRT from the Dell.

-digital ;)

---

### Post by bodycoach2 on 2007-06-03
> **jgrabham said:**
> Puppy, although it feels like win95 with lots of strange apps :]

I second the Puppy vote. I've run the distro on a very similar machine, and it does pretty much everything anyone needs. The 'strange' apps are very minimalistic to keep disk space to a minimum.

If possible I recommend:
[LIST=1]
[*]Set the bios to boot from CD -If possible
[*]Download and burn a copy of dban (Darik's Boot and Nuke)
[*]Run dban on that machine
[*]Burn a copy of Puppy
[*]Run Puppy Linux FROM the CD. Don't bother installing to the hard drive. Puppy actually runs faster from the CD
[*]Increase the size of the Puppy save file to the size of the hard drive
[*]When it's time to upgrade, just burn the new copy of Puppy
[/LIST]

I've set up a few older laptops with this setup, and it works perfect.

---

### Post by iamdigitalman on 2007-06-03
couple problems with your idea:

1. they will be using the optical drive, so running it from the CD is a problem
2. ther CD drive is not bootable. I end up using a floppy image called the CD-ROm God, which has the driver on it, and once it boots the floppy, a program runs that checks for a bootable CD, and if it finds it, it passes booting off to the CD drive.
3. Thus, if I need to keep both teh CD and floppy drive in use to run the OS, they can not be used for anything else.

-digital ;)

---

### Post by RAV TUX on 2007-06-04
> **iamdigitalman said:**
> Ok, sorry if this is in the wrong place, but is it not a forum to ask questions about ubuntu on dells?

anyways,there is this old family Dell Optiplex GXM 5166, and I have had it run a multitude of windows versions. 2000, ME, 98SE, and it originally came with 95. I did a clean install of 98SE, and with the virus scanner and office suite, it is acting very bogged down. Firefox is also acting wierd, crashing 2 or 3 times an HOUR!! So, getting sick of all the viruses and other crud, I figured I will try Ubuntu on this old beast.

It has very tiny specs, and I don't know if xubuntu will play comfortably. here are the specs:

pentium I 166mhz
64mb (4x16mb) RAM
2gb HD
3 ISA, 2 PCI/IDE combo expansion connectors
floppy
CD-ROM
USB 1.1 PCI card
SMC 10/100mbps LAN card
S3 Trio 64v+ (or something like that) video, 1mb of VRAM built in
2 serial ports built in
1 parallel port
built in soundblaster
2 PS/2 ports
built in 10mbps RJ-45/LAN jack

so yeah, not the best specs, but all it will do is browse the web, check email, and write papers and such. 

I want to try fluxbuntu, but I don't know if it's finished, and I don't want to run beta software, and I don't know if it is an offical version of the ubuntu project.

any thoughts?

-digital ;)Your best option for your old computer is [**[B]Wolvix**[/B]]("http://wolvix.org/").

Specifically  [Wolvix Cub]("http://wolvix.org/node/373").

Now if you insist on a Debian based version of Linux,   **[[B][B]Damn Small Linux**[/B]]("http://www.damnsmalllinux.org/download.html") [/B]would be you best option, but I can not stand behind it like I can with [**[B]Wolvix**[/B]]("http://wolvix.org/").

---

### Post by iamdigitalman on 2007-06-04
Thanks. Looks like I have a few options. just wait till I get the machine back online, burn a few CDs, and report which one works the best.

-digital ;)

---

### Post by iamdigitalman on 2007-06-06
here's the results:

-xubuntu alternate CD entered low ram mode, got past the partitioning bit, and paniced.
-DSL gave me a CRC error 90% of the time after selecting my video resolution. Only got it to get past that twice, but in both cases it paniced at a later point.
-wolvix actually works!!-- to a point. I am able to login as root, then when typing startx, it gives me an error that the connection was reset by peer. it is in CLI mode, no gui when booted from CD. how do I install to the hard drive from here?

-digital ;)

edit: never mind, i'm an idiot. screen resolution was set too low to read the directions. it's booting now, and I have instructions on how to install to the HD.

-digital ;)

---

### Post by iamdigitalman on 2007-06-07
ok, I got wolvix cub fully booted off the liveCD, ran the installer, but ran into a problem: the screen resolution is set to 640x480, and I can not change it. This makes it impossible to move to the bottom of the installer window to actually *Start* the installation. I tried manually entering as much data as I have for the video card and monitor. I KNOW it can do up to 1024x768, but only at 256 colors. Once I saved the config file, and typed startx, it kicked back with a "connection reset by peer" message.

any ideas? I am REALLY close to having a feasable linux distro (abeit not ubuntu based) running.

btw, I tried the flux option as well, which I have heard good things about, but it kicked out after it drew the mouse pointer and the monitoring data. I can only get it to fully boot in xcfe.

or should I just try the fluxbuntu beta?

-digital ;)

---

### Post by octathlon on 2007-06-07
You'll probably have to ask that question in the Wolvix forums.  With such an old system as you have, you will probably just have to keep trying different small distros until you find "the one".  Or,  Debian or a server install of Ubuntu and adding a lightweight window mgr might work pretty well.

---

### Post by iamdigitalman on 2007-06-07
UPDATE: ok, I scrapped wolvix cub. I found puppy linux, and am quite happy with it. I am blown away with the speed, even on such an old system. it displays at 800x600, unlike wolvix. I am having some issues getting it installed, but I am asking the fine folks on their own forums.

-digital ;)

---

### Post by reckless2k2 on 2007-06-07
i had success running something of similar spec with damnsmalllinux

---

### Post by Stew2 on 2007-06-08
You actually don't even have to bother installing Puppy to the hard drive. It loads totally into Ram. Once the OS is booted up you can remove the Puppy disc and use your drive for burning CD's, ripping/listening to music etc. The Puppy disc doesn't have to remain in the drive for the OS to work. Just has to be in when you boot up. I'm playing around with Puppy right now... first Linux OS I have used that I can get my wireless cards to work in. Plus it is insanely fast! :D Hope this helps!

---

