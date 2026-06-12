---
title: "stuck in 640x480, unless..."
date: 2005-09-02
forum: Desktop Environments
---

### Post by soulglo83 on 2005-09-02
I have what X correctly recognizes as an IBM G72 monitor, which assuming is plugged directly into my video card initializes correctly and displays in my native resolution 1280x1024.  I however, run a gentoo machine by its side, and love using an IOGEAR KVM switch, to switch between machines, using the same monitor, kb, mouse, and sound.  however, when my ubuntu rig boots with the kvm attached intermediately with monitor and radion 7000 video card, i am stuck in 640x480, and x crashes if i force it to use 24 bit depth.  I have added the hsynch and vsync to xorg.conf and have reduced the optional resolution settings to soleley 1280x1024. So long as i unplug the monitor and boot with it attached directly it is great, i can run it in high resolution, but if booted with the kvm attached, im in 640x480 and i can't change it. i can then unnatach it and run it thru the kvm and still have my high resolution, i just cant boot with the kvm attached.  Is it possible to save the monitor settings that xorg uses or whatever once booted with the monitor attached directly, then force the machine to load them in subsequent boots? if i am shy of any info please request it, i will also append my xorg.conf if requested. thank u in advance!

---

### Post by soulglo83 on 2005-09-03
i wasn't really sure anyone would be able or know how to help, unfortunately im giving up on ubuntu, 640x480 isnt cutting it.  im going to give the new vista beta a try, i hear its going to make windows a lot more like linux/os x. thanks anyway

---

### Post by AndrewB on 2005-09-03
funny thing, my desktop came up in 640x480 this morning. I gave it a hard reset/reboot, and it came up in 12XXx res. Strange. Looking forward to Breezy.

Peace

---

### Post by nobody123 on 2005-09-04
[QUOTE=AndrewB]funny thing, my desktop came up in 640x480 this morning. I gave it a hard reset/reboot, and it came up in 12XXx res. Strange. Looking forward to Breezy.[/QUOTE]

Did you leave your monitor turned off when you booted your machine?

---

### Post by soulglo83 on 2005-09-04
this happens after rebooting, after dpkg-reconfiguring, and after any other hoogaggery i have tried, i have looked through and tried what is in so many wiki's and i can pin point the problem, ubuntu is not loading x with the paramaters it receives from my moniter, but those from the kvm, it claims it recognizes the moniter, but the refuses to let me out of 640x480, what i  neeed to do is force the machine to think the moniter is connected directly and to ignore the kvm.

---

### Post by soulglo83 on 2005-11-07
ok i have given enough time after the breezy upgrade this time, as to say, not trash my install like it did when i jumped into hoary stable. i love this os so much im not willing to give up, even though i have to risk the life of my vga cable, or card just to get my x server to recognize my moniter ( i have to unplug the moniter from the kvm switch and plug it directly into the vga card ) then ctrl+alt+backspace at either gdm or gnome to restart x, then after x is restarted i can swap the cable back into the kvm and ubuntu will act like it should, in a much higher and thus nicer resolution.  this has become frustrating as all hell, as my vga cable pins need to be manually straightened constantly, and replacing that is going to be a very unnecessary consequence of my love for this os. no other linux os's even, the kubuntu install exhibit this behavior. only stock ubuntu and edubuntu. i am growing hopeless and this all seems like such an easy fix for u veterans out there, to force my x server to recognize certain settings, instead of probing for new ones. please i am sooooo desperate for a fix to this, before it is too late!

---

### Post by linker3000 on 2005-11-25
Well, this was driving me mad until I finally tracked down a fix:

My evaluation system has an integrated Intel video chip (82854G/GL). To get up to 1280x1024 resolution, I had to do the following:

1) Reboot the PC and enter the BIOS setup program

2) Find the setting for amount of RAM allocated to the video chip and change it from default (512K!!) to 8MB

That was it! Now I am offered resolutions up and beyond 1024x768

While I was experimenting, I also changed the video driver in xorg.conf from 'i810' to 'vesa' but after the BIOS RAM change I put it back to i810 and it's still working fine.

Hope this saves someone some time!!

L3K

---

### Post by KermitJr on 2005-12-01
I was having trouble with several older video cards and a particular monitor and kept getting 640x480 no matter what I did for modes, etc.  

HOWEVER, when I went back one time and ran
```
sudo dpkg-reconfigure xserver-xorg
```

I entered the actually amount of RAM on the video card (one was 4096 and another 2048) and PRESTO! My Modes line worked as normal with or without monitor on boot.

Glad you figured it out on your own, though.

Also, you can troubleshoot in the future by looking for the actual error messages in the /var/log/X11/xorg[tab].log file.

Hope this helps!
KermitJr

---

