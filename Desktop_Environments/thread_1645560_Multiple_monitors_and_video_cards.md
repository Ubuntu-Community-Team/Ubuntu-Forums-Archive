---
title: "Multiple monitors and video cards"
date: 2010-12-14
forum: Desktop Environments
---

### Post by crepincdotcom on 2010-12-14
Hey all,

I've been using linux for roughly 12 years now but I've always avoided linux on the desktop since touching X back in the day was quite a hassle. I recently decided that rather than keeping my windows desktop full of 15 PuTTY instances, I should rock the *nix desktop.

I started by installing Ubuntu 10.10 Desktop. It detected my two monitors handing off a pci express card just fine. I decided to install the ATI drivers when it prompted me - the proprietary drivers would let me select to use the monitors separately, but would always just default back to mirroring the screens. I was unable to get it to stop that, so I had to go back to the open source drivers. Which is fine, I don't really need the 3d accel.

Roll forward a week, I ordered another video card to add another screen. I purchased another ATI card, since word on the street is that same-vendor chipsets play best together. This one had to be PCI, if this matters.

dmesg reports the new card is fine and happy, but the Monitors GUI thing doesn't detect any monitors off the new card, or report anything about it. So: what should I do to make the second video card get noticed?

Here's my dmesg output if it helps: [http://pastebin.com/E0Uq86w2](http://pastebin.com/E0Uq86w2)

Thanks, 

-Jack

---

### Post by 3Miro on 2010-12-14
I have been running two monitors on the same Intel video card for some time now and I never had trouble. Monitors on different cards are a different animal. 

First you can go to the terminal and try playing with xrandr. Try
```
 xrandr -q 
```
to see how many monitors are detected. You can also look at the other options given by xrandr:

[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)

Then try to see what happens if you try to boot with the new card only, just to make sure it works.

If both cards work individually, but not together, there may be a question of different GPU architecture. What are the models of the two cards.

---

### Post by crepincdotcom on 2010-12-14
Ah, very good call - while both are detected by the kernel, xrandr only sees the pci-e card:

[http://pastebin.com/yvyEgg9U](http://pastebin.com/yvyEgg9U)

The 'new' PCI card is a "SAPPHIRE 100262PCIL Radeon HD 2400PRO 512MB 64-bit DDR2 PCI HDCP Ready Video Card". The 'old' pci-e card (the working one) is a "Radeon HD 2400 Pro".

-Jack

---

### Post by 3Miro on 2010-12-14
Hm, same model, so card conflict is not the problem. And you are using the open source driver too ... I use Arch on my laptop, so I don't know about Ubuntu, however, Arch gives me image on both monitors during boot time. Double-check to see if you get image from just the new card installed (there may be a defect in it that the kernel doesn't detect but causes xorg to fail).

With the FOSS driver, things should have been picked up automatically, but apparently not. You can try to reconfigure the xorg-server:
```
 dpkg-reconfigure xserver-xorg 
```
WARNING: do this only if you are using the FOSS driver. Do not do this if you have the ATI proprietary driver.

Other than that, manual configuration of xorg may be needed and I am not good at that at all.

---

### Post by crepincdotcom on 2010-12-14
> **3Miro said:**
> 
With the FOSS driver, things should have been picked up automatically, but apparently not. You can try to reconfigure the xorg-server:
```
 dpkg-reconfigure xserver-xorg 
```
WARNING: do this only if you are using the FOSS driver. Do not do this if you have the ATI proprietary driver.

Did this and rebooted, no change. Drat.

-Jack

---

### Post by ivicks on 2010-12-15
This could be bios issue such as the board is saying since there is a card in PCI-Express slot use that instead.

You may also want to try something like this in your xorg.conf file

Screen 0	"Screen0"    <-------- This being your primary screen running on the PCIe card
Screen 		"Screen1" LeftOf "Screen0"
Screen 1	"Screen2" RightOf "Screen0"


Just some thoughts

---

### Post by crepincdotcom on 2010-12-19
Thanks a ton for the help guys, with much reading and such I got everything working. 

If anyone is looking through this to fix their stuff later, I went back to the proprietary drivers, which recognized both cards. lspci|grep VGA told me which was which, and the aticonfig --help novel had some handy things in it as well.

-J

---

