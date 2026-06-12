---
title: "LiveCD's XServer crash with ATI Radeon X800XT"
date: 2006-09-25
forum: Desktop Environments
---

### Post by nikdo on 2006-09-25
Hello all,

I'm a total newbie to linux (not pc's tho) who got fed up with windows and wants to join the world of linux.

I have a 2 month old gateway pc - nothing too special:
AMD Dual core 64bit, 2Gig Ram, 200 gig IDE, integrated nvidia card (disabled), with ATI Radeon X800XT PCIe.

This is what I did:

a month ago, I installed ubuntu (32bit version) - worked like a charm (did a dual boot with windows xp that came preinstalled in the pc). I only mention this to show that all hardware on my machine seems to work fine, except the new ATI Radeon X800XL I added later.

Few weeks later, I added an ATI Radeon X800XT video card. Then I couldn't boot no longer into ubuntu - got an error with the X-server. So I let it be for the moment (and continued using XP for now).

This week I got my books on linux so I decided to get into linux seriously. I downloaded the 64bit version of ubuntu (verified the checksum) and tried liveCD - got the same X-server error. So I researched the net and tried everything that I came across that made sense. I even disconnected my HDD to make sure I was truly just running the liveCD. These are my observations:

When running the liveCD "start / install" it loads everything and then tries to run the x-server. That crashes. It asks me if I want to see the log. This is what the log says:
(EE) No devices detected

When I check to see the details on the next screen, this is what is shown:

(II) Primary Device is: PCI 02:00:0
(II) Candidate "Device" section "Ati Technologies, Inc. R430 UM [Radeon X800 XL] (PCIe)".
(WW) ATI: PCI Mach64 in slot 2:0:0 could not be detected!
(WW) ATI: PCI Mach64 in slot 2:0:0 could not be detected!
(EE) No devices detected

Fatal server error:
No screens found


Now I know lots of people have been having this problem. But all the solutions seemed to be for folks who already had ubuntu installed and their x-server messed up after that. So they all got the advice on how to use the commands to install a new driver. But I am not even that far! I need first to be able to install ubuntu. I don't see how I am supposed to go and install all these new drivers, then reboot - as soon as I reboot, I of course looose all the updates, since this is an install I am doing and nothing is on the HDD yet.

Please disregard the fact that I installed ubuntu before. As I said, I tried installing ubuntu without HDD (just to see if I'd get past the x-server error) and I still have the same problem.

If I try the "vga" option, it makes no difference. I also tried the "safe mode" - it boots, shows black screen, and the music plays for when ubuntu loads - but the screen is utterly black.

Any help would be tremendously appreciated.

-nikdo-

---

### Post by dickohead on 2006-09-25
Use the integrated NVidia and watch it work! The problem is that ATI support for Linux is still lacking. Your best bet is to either - reinstall ubuntu and use the "vesa" driver option in the xorg.conf file OR update your existing installation so that you have some ATI drivers and edit the xorg.conf file accordingly. There are many atricles out there discussing howtos for ATI cards with Linux and Ubuntu.

---

