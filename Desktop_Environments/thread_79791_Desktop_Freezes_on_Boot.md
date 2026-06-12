---
title: "Desktop Freezes on Boot"
date: 2005-10-20
forum: Desktop Environments
---

### Post by Scabby_al on 2005-10-20
While I'm a Windows support tech at work, I refuse to be without Linux in some fashion. I have a second computer, an HP Compaq DX2000 desktop. Its a 2.8GHZ P4 with a 128 ATI PCI card. Anyhoo, Ubuntu installs fine until it gets to the "hotplug" portion of the boot screen and then freezes.

Has anyone had a similar problem or have any ideas on how to fix it? I'm fairly loyal to Ubuntu and would prefer not to switch distros to get it to work.

---

### Post by Dr. Nick on 2005-10-20
Ive heard ctrl+C will skip parts of the bootup but havent tried yet, I know this isnt a permanent fix but may help you continue booting to see logs. I havent had the problem so I dont know a fix.

---

### Post by fimbulvetr on 2005-10-20
I believe there is a kernel option for nohotplug, try passing it on the command line.
Do you have a pci video card in there you are using while there still is an onboard one? I've seen the problem happen in that case.

---

### Post by Scabby_al on 2005-10-21
[QUOTE=fimbulvetr]I believe there is a kernel option for nohotplug, try passing it on the command line.
Do you have a pci video card in there you are using while there still is an onboard one? I've seen the problem happen in that case.[/QUOTE]

yeah, the onboard video is still on. There really isn't a way to deactive it; you either have onboard or ornboard/PCI.

I'll try removing the PCI video and see what happens.

---

