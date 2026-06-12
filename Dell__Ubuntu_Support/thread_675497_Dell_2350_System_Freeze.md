---
title: "Dell 2350 System Freeze"
date: 2008-01-22
forum: Dell  Ubuntu Support
---

### Post by maelstrom_p-90 on 2008-01-22
So I just got this old Dimension 2350 dell for a song cause the windows partition was so ****** up with spy ware up the yazoo and what not.  So i decide to take and have Linux, specifically Ubuntu Feisty Fawn (7.04), put on it cause i don't even wanna start bothering with windows and spy ware and viruses that have been put on there in the last 3 yrs unchecked or fire walled while the previous owners watched porn form sites who's sole intentions were to mess with you system.
So I take my Ubuntu cd and plug it into the damn thing and do the whole boot from CD and come to the classic start up screen that says like 'check cd for defects' and 'start or install Ubuntu', all is swell thus far, right. and then i select 'start or install Ubuntu' and I come up with this blank screen, so im thinking 'oh this system is just old maybe if i let it sit there for a second it will come up with the Ubuntu desktop right, but that does not happen it just stays blank.
So then i think to myself that it must be the cd cause i do this like 3 times in a row.  I then plug the cd into my newer system a Compaq Presario and boot from the disk and the disk is fine not a thing wrong with it, i can boot from it and check it for defects and all is well but it just doesn't work on my dell.

If somebody could help me out with this problem I would be much obliged thax for reading.

---

### Post by ATIuser on 2008-03-09
it seems so far that the only way that anyone has been able to boot from the live CD and install *any* Linux distro on a Dell Dimension 2350 is by going into BIOS and specifically selecting the onboard graphics rather than the "auto" setting.

If you need to upgrade your BIOS, there is a download on the Dell site for revision A02, which is the latest and probably the last revision that will ever be made for this crap PC.

---

### Post by Tuxtur on 2008-04-02
I realize I'm posting to a dated question but maybe this answer will be useful to someone anyway.

Dell Dimension 2350 with a graphics card won't boot. Sorry to say I'm not technical enough to offer a great explanation but it appears to me that the Dell bios doesn't do enough to "hide" the onboard video from Linux, and that causes a kernel panic when it finds the combination onboard and video card. There are two "fixes" for this that I know of:

1. You can go into the bios set the video to use the onboard graphics. You don't necessarily have to remove the graphics card, it works with it in or not. Besure to move your monitor cable to the onboard video port.

2. If you insist on keeping your video card try the following steps:

a. set the bios to use the onboard video, move the monitor cable to the onboard video port.

b. install ubuntu, it should work normally.

c. next in terminal type "sudo nano /etc/modprobe.d/blacklist"
add these lines to the end
"blacklist agpgart
"blacklist intel_agp"
those entries should force Ubuntu (and most Linux distros) to ignore the onboard video preventing the kernel panic system hang. 

d. Install your video card drivers.

e. restart PC, in bios change video to "auto" and move your monitor cable to the video card port.

---

### Post by slockton on 2008-04-09
Thank you! It solved my problem.

I was having a very similar issue with an old HP d220 with a GeForce FX5500 PCI card. I was totally locking up during boot. I was starting to suspect it was a conflict between the on board video (which you also cannot turn off, only de-prioritise) and the PCI card - I then found this thread.

Thanks again,
Ste

---

### Post by Tuxtur on 2008-04-11
slockton: I'm so glad that worked out for you! It's always nice to hear about it when you can help someone.

---

### Post by tdoyle on 2008-07-10
> **ATIuser said:**
> it seems so far that the only way that anyone has been able to boot from the live CD and install *any* Linux distro on a Dell Dimension 2350 is by going into BIOS and specifically selecting the onboard graphics rather than the "auto" setting.

If you need to upgrade your BIOS, there is a download on the Dell site for revision A02, which is the latest and probably the last revision that will ever be made for this crap PC.

hello, I'm new to Ubuntu but experienced PC user.  Have 2350 in good condition, latest BIOS (A02), with BIOS set to "onboard" graphics rather than "auto".  Still no luck, blank screen after CD spins for a while.  Confident that 2350 hardware is in proper working condition.  Any more suggestions?  Thanks in advance for any help.

---

