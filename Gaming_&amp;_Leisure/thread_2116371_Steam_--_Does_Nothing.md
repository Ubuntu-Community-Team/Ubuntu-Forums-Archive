---
title: "Steam -- Does Nothing"
date: 2013-02-15
forum: Gaming &amp; Leisure
---

### Post by CalmDownMonkey on 2013-02-15
I saw Steam now officially supports Linux, so I booted into Ubuntu 12.10 to test it.

I thought I'd download a simple game for the trial run -- "Faster than Light".

I wasn't very surprised to see that attempting to launch the game does nothing. For a fraction of a second, it reports to my friends that I am playing "Faster than Light", then immedietely cancels back to my normal status.

Am I missing a crucial step in the Steam installation proceedure? Or should I stick with Windows for pain-free execution of simple indie games?

Thanks =)

---

### Post by Perfect Storm on 2013-02-15
Have you checked these existing threads?
[http://ubuntuforums.org/showthread.php?t=2116282](http://ubuntuforums.org/showthread.php?t=2116282)
[http://ubuntuforums.org/showthread.php?t=2116295](http://ubuntuforums.org/showthread.php?t=2116295)

---

### Post by CalmDownMonkey on 2013-02-16
Thank you so much for trying to help...

I'm pretty sure it's is a driver issue with my ATi HD 4890.

I've spent several hours going round in circles following different guides to get the right drivers in, but they all end up in an error or a dead end one way or another.

Unfortunately, I think trying to get anything to work on this OS under this hardware is going to be far too much of a time sink for me, so I think I'll leave the installation dormant and try again some months down the line.

Thanks again though =)

---

### Post by rudeboyskunk on 2013-02-16
Run Steam from a terminal, launch FTL, then post the output here so we can see exactly what the error is.

---

### Post by holastickboy on 2013-02-16
> **CalmDownMonkey said:**
> Thank you so much for trying to help...

I'm pretty sure it's is a driver issue with my ATi HD 4890.

I've spent several hours going round in circles following different guides to get the right drivers in, but they all end up in an error or a dead end one way or another.

Unfortunately, I think trying to get anything to work on this OS under this hardware is going to be far too much of a time sink for me, so I think I'll leave the installation dormant and try again some months down the line.

Thanks again though =)

AMD, not Linux or Ubuntu, has discontinued support for all video cards before the HD5XXX series.  That means that the HD 4XXX series are now stuck on legacy drivers (this is also the case for Windows).

Most of the guides that show you how to install the drivers are for supported cards. Sucks, but true!

---

### Post by CalmDownMonkey on 2013-02-18
Aha... in that case, I think I've royally screwed my graphics drivers by trying to follow these guides. Well, I know I have -- it gives me some warning about running in low graphics mode, then freezes :oops:

> **rudeboyskunk said:**
> Run Steam from a terminal, launch FTL, then post the output here so we can see exactly what the error is.

Thanks, I didn't think to try this... I will download and reinstall Ubuntu now and give it a try. 

If my card is no longer supported, is it likely I won't be able to use Steam, even to play simple games like FTL? Maybe support from people like AMD will improve now that there's an easy platform for buying/playing games on Linux?

---

### Post by CalmDownMonkey on 2013-02-18
I just remembered, I have a triple-boot setup that I created through a Windows utility called EasyBCD (Windows 7, Windows XP, Ubuntu).

I seem to remember it being a hassle to set that up, so is there a way I can reinstall Ubuntu without it affecting any of the boot-related stuff? I'm worried if I reinstall Ubuntu I'll lose access to my Windows installations. Thanks!

---

### Post by xREDEMPTIONx on 2013-02-19
Why worry about Ubuntu affecting the boot related stuff? Just let it install the grub bootloader and it will pick up W7 and XP just fine. You can customize the boot menu very easily afterwards with grub customizer. Much easier than messing with easybcd and the windows bootmanager imo. 
  
But to answer your question, yes you can reinstall without installing grub. Select manual partitioning in the install and where you choose your partition there is a dropdown box for the location of the grub install. Install it on the same partition of your ubuntu install.

---

