---
title: "Can't update from Ubuntu 10.04 to 10.10"
date: 2011-02-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by perolad on 2011-02-18
Or should I even bother trying?

I have a Dell v130 laptop and a Dell Dimension 7100 that both came with Ubuntu 10.04 LTS installed.  I'd like to go to 10.10, but perhaps newer isn't always better.  Nonetheless, looking at the Apt info in Package manager, I see that there are a number of previous versions starting with v7.xx there, that were probably used by the Dell guys to step up to 10.04.  Maybe they have conflicting dependencies that as a newbie, I have no idea about.  If so how to resolve that matter?

Anyway, when trying to go from 10.04 to 10.10, I followed all the instructions I could find online to no avail always to return to this error message:

 "An error occurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong. The error message was: 'Error: Marking the upgrade. (E.Error, pkgProblemResolver:Resolve generated breaks, this may be caused by held packages.)' This usually means that your installed packages have unmet dependencies." 

As an eager newbie to Ubuntu Linux, my only response after trying a bunch of things is, "Huh?"

Can anyone please explain how to jump through these hoops, or even if I should try at this point?

Thanks in advance,

Per

---

### Post by emptythevoid on 2011-03-01
I don't know for sure, since the Dell laptops I have didn't come preloaded, but I know Dell uses custom installs of Ubuntu when they come preloaded.  I'd wager the reason you can't upgrade is because of this custom Dell install (one of the reasons they like to use long term releases - they can test that it works and expect you to *not* upgrade)

If you really want 10.10, you could go about doing a fresh install.  Just make sure you read the release notes for 10.10 first.

Update:  [http://www.ubuntu.com/certification/hardware/201010-6596](http://www.ubuntu.com/certification/hardware/201010-6596)

---

### Post by LeftWIngPenguin on 2011-03-02
I've been having this same problem, so I'm interested. Would creating a fresh install disk and installing from that erase all my documents and settings?

---

### Post by KegHead on 2011-03-02
Hi!

You may need to install a fresh 10.10.

Also, make a complete backup of all of your important files.

KegHead

---

### Post by emptythevoid on 2011-03-02
You can usually do just fine doing a fresh "vanilla" install of Ubuntu.  Just know that if Dell did any special tweaks to their (old) version, those tweaks may not work with a fresh install.  For example, I think the Mini 9 Ubuntu 8.04 came with the proprietary fluendo codecs.  

Do check the release notes.  Another Mini 9 example is that it uses a broadcom wireless card.  You need to hook the Mini 9 to the internet to get the driver to start working, which you wouldn't have experienced with Dell's custom image because they made sure it was going to work (or should have, at the least)

---

### Post by pieisgood4589 on 2011-03-02
> **perolad said:**
> Or should I even bother trying?

I have a Dell v130 laptop and a Dell Dimension 7100 that both came with Ubuntu 10.04 LTS installed.  I'd like to go to 10.10, but perhaps newer isn't always better.  Nonetheless, looking at the Apt info in Package manager, I see that there are a number of previous versions starting with v7.xx there, that were probably used by the Dell guys to step up to 10.04.  Maybe they have conflicting dependencies that as a newbie, I have no idea about.  If so how to resolve that matter?

Anyway, when trying to go from 10.04 to 10.10, I followed all the instructions I could find online to no avail always to return to this error message:

 "An error occurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong. The error message was: 'Error: Marking the upgrade. (E.Error, pkgProblemResolver:Resolve generated breaks, this may be caused by held packages.)' This usually means that your installed packages have unmet dependencies." 

As an eager newbie to Ubuntu Linux, my only response after trying a bunch of things is, "Huh?"

Can anyone please explain how to jump through these hoops, or even if I should try at this point?

Thanks in advance,

Per

This problem is incredibly common amongst any upgrades, especially from 10.04 to 10.10. I myself had this exact problem with the exact same error readout.

The problem seems to stem from the fact that Dell, or yourself, put in extra unofficial non-community-supported repositories. Removing these would solve your problems.

Alternatively, to avoid the headache, why not just burn a copy of the Ubuntu 10.10 alternative install .iso and upgrade it from that?

---

### Post by mosaic2s on 2011-03-02
suggest to stick to 10.04 if you are looking for a working system. i used 8.04 and shifted to 8.10 that stopped many printing options for me. now 10.04 - is stable and works for me. allowing me to try other stuff on a stable OS instead of forever tweaking and searching for solutions.

if you still wish to try 10.10 for its promises, go for dual boot. set up 10.10 as a fresh install in a new partition. that should work.

---

### Post by nm_geo on 2011-03-03
> **mosaic2s said:**
> suggest to stick to 10.04 if you are looking for a working system. i used 8.04 and shifted to 8.10 that stopped many printing options for me. now 10.04 - is stable and works for me. allowing me to try other stuff on a stable OS instead of forever tweaking and searching for solutions.
 
if you still wish to try 10.10 for its promises, go for dual boot. set up 10.10 as a fresh install in a new partition. that should work.
 
+1 on the dual boot. But beware you may become a multiboot junkie let's see I have 5 versions of Ubuntu on my laptop right now...:D
 
Start with a live/USB with Maverick on it and boot to it and check it out knowing it will be slower than installed. All you need is an ethernet cable and DSL outlet. If you like it you can use GParted from the USB to resize partitions and install in the freed space.
 
That would be the best way to really see if Maverick 10.10 worked for you. I checked some specs on the DellV130 and it looks like you have an Intel wifi card that should be good for both versions, and I believe you have 250GB HD space so if you are not a picture or music nut you should have the space.

---

### Post by perolad on 2011-04-24
> **KegHead said:**
> Hi!

You may need to install a fresh 10.10.

Also, make a complete backup of all of your important files.

KegHead

Sorry, took me awhile to find this response.  Since I have both a laptop and a desktop with Dell Ubuntu 10.04 distros -- reason is that I ordered the Vostro laptop and they shipped the desktop by mistake.  When I wanted to return it they said they'd cut the price in half if I kept it and ordered the laptop--so I couldn't say no to a Dell Studio XPS for less that $200.  :)

Anyway, for now I'll concentrate on the Vostro and tackle the XPS later.

It appears from the specs that I just dug out that Dell installed a proprietary version of Ubuntu 10.04 LTS to wit:

Vostro V130n laptop
6-cell battery
2.0 GB DDR3-1.333MHz SDRAM on 1 DIMM
Intel Celeron Processor 1.06 GHz, 800 MHz FSB
Intel Graphics Media Accelerator
Dell 1.0 MP Camera
250 GB 5400RPM SATA HDD
Dell Wireless 1702 802.11n/NT3.0 Network Combo Card
UBUNTU 10.04 Linux _**VOSTRO**_

So, it seems that is the reason some of the Cannonical repositories return an error, plus probably the reason that I can't upgrade from 10.04 to 10.10.  Hence the solution, eventually, will have to be a fresh install.

The laptop has no DVD. I imagine I would have download a new Ubuntu ISO distro to my XP machine, then somehow "burn" it to a suitably sized USB stick.  Dunno how to do that.

Also, is an XP NTFS 32-bit file system ISO  transferred to a thumb drive compatible with the Linux laptop file system which I realize is quite different?  I also believe the Vostro is 64 bit, but not absolutely sure and wondering how to get that info off the machine.  In any case, does any of that matter once I figure how to burn an ISO to XP USB then pop it into the laptop, boot from the USB thumb drive and somehow load the new distro from there?   Do I have to reformat anything--or whatever Linux does?   No important files to back up--still fiddling with the nuts and bolts on the laptop in my spare time--so I have little to lose.  Haven't even figured out yet how to network the Linux machines into my Windows LAN but that's not important for now.  :)

I'd be grateful for any advice.

Thanks,

-Per

---

