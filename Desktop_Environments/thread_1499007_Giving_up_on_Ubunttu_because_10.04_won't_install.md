---
title: "Giving up on Ubunttu because 10.04 won't install"
date: 2010-06-01
forum: Desktop Environments
---

### Post by Randy Schilling on 2010-06-01
I tried upgrading 8.04 to 10.04.  This failed wiping out my XP installation. Problems described in questions 111958 and 112061..  

Ive reinstalled windows, noted that the web site for download and instsall of 10.04 changed, I gave 10.04 another try.  This time I downloaded the iso file and made a live 10.04 cd.  But my system stalled at the first screen, the purple one with the word ubuntu above 5 dots, when I tried to boot from my newly made live cd.

My system has a problem with 10.04, not all ubuntu.  8.04 installed from live cd without a problem.

It appears that I can't grow with ubuntu.  Unless someone can tell me how to install ubuntu on my system (and I'm genuinely hoping someone does just that), I'm going to migrate to Fedora or another Linux distribution.

---

### Post by captain_conrad on 2010-06-01
Hey man

don´t give up so easily! I can tell u right now ubuntu is the most user friendly linux distro out there and its the one distro that you´ll get the most support and help for.

Go to the ubuntu website itself and read the ¨update notes¨. I was running 9.04 and wanted to update straight to 10.04, and they advised against that, they advise updating your ubuntu one step at a time, in other words I had to update 9.04 to 9.10, and 9.10 to 10.04. I think the only way you can jump from 8.04 to 10.04 is by formatting your ubuntu hard drive partition clean clean (obviously after backing up all your personal data to cd/usb/whatever), and do a fresh install.

I have a dual boot with windows vista and ubuntu, and I use this thing called grub. It stands for grand unified bootloader. Google it and find out more about it. Try it even. Somebody else set mine up for me so i dont know how it works, it just works. When i switch my computer on, it lets me choose if I want to boot ubuntu or vista. It has also protected my vista boot through many ubuntu upgrades and many cockups on my part.

Anyways just keep trying, keep searchin through threads here on ubuntu forums, keep posting your experiences and im sure you´ll figure it out :)

---

### Post by howefield on 2010-06-01
> **captain_conrad said:**
> I think the only way you can jump from 8.04 to 10.04 is by formatting your ubuntu hard drive partition clean clean

Direct upgrading from 8.04 to 10.04 is perfectly doable and is supported, (LTS to LTS release)

@OP, when booting with the 10.04 live CD, try pressing F6 after selecting your language, and select the nomodeset option. Then continue booting, if that doesn't work, press the Esc key after pressing F6 as above, and remove "quiet splash--" from the end of the boot line.

---

