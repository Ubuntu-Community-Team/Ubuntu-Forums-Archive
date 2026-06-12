---
title: "problems installing Gutsy on Dimension 8300"
date: 2007-12-02
forum: Dell  Ubuntu Support
---

### Post by neatokino on 2007-12-02
I'm trying to install Ubuntu Gutsy (dual boot with XP) on a Dell Dimension 8300, 2.6GHz processor, 512MB RAM,  Nvidia GeForce FX5200 graphics card.  I've been through so many different attempts to install, I'm about ready to throw the computer out the window.

I have tried installing with the Unbuntu Gutsy LiveCD, with the Alternate CD, with the OpenSuse 10.3  LiveCD, the OpenSuse DVD, the latest version of Mandriva LiveCD and the latest Mandriva DVD, and each time I get some variation of the same problem:  a couple minutes into the install, the screen starts to get 'snowy' and then skews all over the place, then blinks to black, then back to snowy picture, then goes completely black.  This happens when I choose safe video,  text install, vesa, etc etc. 

None of the live CD's make it past the initial stages except, curiously, the Mandriva One Live CD.  That works as a Live CD, but I still haven't been able to install it.  Oh, and Ubuntu is absolutely the distro that I want to be using.  

I managed to repartition the hard disk with gparted (barely), but that went snowy on me, too, and the screen went black just after the repartitioning was done.

I can't figure out what the hardware issue might be, as the computer works perfectly with Windows XP.  Graphics are good, sound is good, the CD player works... no issues whatsoever.  Except, of course, I'm not interested in running Windows as the principal operating system on this machine.

I posted my problem on the Absolute Beginner forum, but got no help.  This is frustrating beyond belief, and it's difficult for me to imagine that this computer is incapable of installing linux.

Can someone PLEASE offer me some kind of help????

Thanks in advance,

Michael

---

### Post by joachi on 2007-12-16
Did you try doing a <Ctl> <alt> <F4> to see what the log is telling. I am kind of in the same boat with a Dell Dimension 4100 with 512 Meg Of Ram. When it tries to install the kernel image it just quits. I think it has something to do with the amount of memory. I have successfully installed in other machines. Just not on one with 512 Meg of RAM.

On that note I would also like to know how to fix the problem. For me the Live CD works fine. I just cannot install or upgrade.

7.04 has been painful on my machine. fontcache continually crashes. Now my Firefox dies frequently especially with the new and improved yahoo pages. :confused: Completely at a loss. I have a few core files in the /var/crash directory. Don't know how to read them into a gdb so I can look at what is going on....

---

### Post by neatokino on 2007-12-18
I didn't solve the problem so much as work around it.  I upgraded memory to 1.5Gig, and I bought a new graphics card, a GT7300;  I figured both to be useful upgrades anyway, and they weren't expensive at all.

Once I made those changes, the live cd worked, and I went ahead and did a regular install, which works fine except for my wireless issues, which are unrelated.  Since I did the memory upgrade and the video card at the same time, I don't know which solved the problem.

---

