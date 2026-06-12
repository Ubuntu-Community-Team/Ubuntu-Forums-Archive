---
title: "Gamer switching to Linux"
date: 2015-09-03
forum: Gaming &amp; Leisure
---

### Post by Aidan_Owen on 2015-09-03
Hi, I'm brand new to Linux, at least as a daily driver. I used it in the 11.04 days and got pretty good with ```
sudo apt-get install package-name-thingy
``` but that's really it. :P

The one issue that's really making me a little uneasy about this switch is compatibility with games. I own 25 games but only 12 are able to run natively, and one runs very well in Wine (so I hear). Of course the other 13 games that do NOT work in Linux with Wine or native support are the ones I play most often, such as GTA V, Payday 2, and Skyrim. [CENTER][COLOR=#000000]](*,)
[/COLOR][/CENTER]
Any tips or tricks would be appreciated :biggrin:

---

### Post by PaulW2U on 2015-09-03
*Thread moved to **Gaming & Leisure**.* 

Please give us some further information about the particular problems that you're experiencing.

---

### Post by Aidan_Owen on 2015-09-03
I'm just a bit uneasy with the fact that my games aren't natively supported and I have to dual boot, was wondering if anyone had any tips or tricks regarding running games. I think I read somewhere about VMs and VT-d and getting native performance in a VM, is that legit?

---

### Post by mystics on 2015-09-03
You're not getting native support in a VM, at least not on Linux. You'd essentially be running a Windows machine inside of Linux, and that can create problems for performance since you aren't taking full advantage of your hardware.

As for help with better support, both Payday 2 and Skyrim have installers with PlayOnLinux, which can make gaming with Wine on Linux significantly easier. Along with being overall easier to use, it also prevents, or at least makes it harder, for Wine settings for one game to break another. It's also likely that the scripts, such as those for Payday 2 and Skyrim, will fix most of the common problems with Wine. If you want to play games on Linux, I'd *highly* advise looking into it. It will make the overall experience much better.

However, I would caution against a complete move to Linux. Like it or not, Windows is still the primary target for gaming. So if you really want to stick to the hobby, don't want to give up any games like Grand Theft Auto V, and/or want to make sure future games are supported, I'd say either dual boot or stick with Windows. If you stick with Windows, you could always use a VM just to play around with Linux.

---

### Post by Aidan_Owen on 2015-09-03
What's the performance like in Wine? I hear it's really slow if the game is too resource-hungry?

---

### Post by mystics on 2015-09-03
It's hard for me to judge just how much performance takes a hit. I generally stick with some older games (not resource intensive) and only have a MacBook Pro right now, and Apple doesn't really build its computers for gaming. I have been able to run some recent indie games (e.g. This War of Mine) reliably without a problem, and I know my computer handled the Mac version of Civilization V decently so long as I didn't play large games. However, when I ran The Witcher in Wine, it couldn't keep a consistent frame rate. Even with all settings at minimum, battles were near unplayable.

That's just my experience for what it is worth. You'll probably have better success if you have a computer more dedicated to gaming since Macs really aren't built for that.

---

### Post by Aidan_Owen on 2015-09-05
thanks :)

---

### Post by MikeCyber on 2015-09-05
I run several games with playonlinux and I would guess FPS loss is less than 10% with my GTX770. No problem for a recent PC.

---

### Post by mastablasta on 2015-09-07
wine is compatibility layer and not an emulator so for some the loss is negligible. check out their application database for more info. the question you need to answer to yourself if why you want to move to Linux? if windows works ok with you and if you game plenty then stay on windows (at least for now). I still run windows XP for the same reason. I can play with Linux in a VM inside windows. the GPU drivers in Linux are not on same level as windows. even NVidia ones are usually worse, but if you have an older PC where you might need opensource drivers.... then its even worse. I bet if I stuck win 8 on this PC it would run better than Linux. poor hardware support is just another minus in Linux.

---

### Post by nargaroth_reg on 2015-09-10
From my experience I'd say it is essential to install play on linux (can be found in the official repositories), the latest version of wine staging (can be installed with play on linux) and propietary gpu drivers in order to be able to play non-native 3d games with acceptable performance. Even then for some of them graphics quality and performance does not match the ones you can get on windows. It is also very useful to read the tips for making games and applications work with wine at [https://appdb.winehq.org/](https://appdb.winehq.org/) . If you don't mind too much about not being able to use 'very high' for all settings then most of times things work acceptably. Older games and games played with emulators usually work as well as on windows.

---

### Post by oldrocker99 on 2015-09-12
I will add that I used the PoL script to install Skyrim, which installs Steam for Windows, from which you install Skyrim. It runs at pretty much full speed for me, and I was able to install Oblivion in the same bottle. PoL is your best friend if (for some reason) you want to use Windows programs.

---

