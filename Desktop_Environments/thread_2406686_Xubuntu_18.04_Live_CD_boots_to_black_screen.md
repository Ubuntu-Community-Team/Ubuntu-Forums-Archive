---
title: "Xubuntu 18.04 Live CD boots to black screen"
date: 2018-11-24
forum: Desktop Environments
---

### Post by fozziebear on 2018-11-24
I am trying to install Xubuntu 18.04 on a Dell Optiplex D620 SSF pc. It has a 3.0 Ghz Pentium D processor and an intel chipset with integrated Intel GMA 950 Dynamic Video Memory Technology 3.0 (specs here [https://www.cnet.com/products/dell-optiplex-gx620-620dmin/specs/](https://www.cnet.com/products/dell-optiplex-gx620-620dmin/specs/).)
The DVD boots to grub screen but then screen goes black. I can see CD and hard drive activity so its still copying files or booting but nothing is shown on monitor.
I have entered the grub boot menu and selected nomodeset in the F6 boot options. This then allows me to see the boot menu such as Try Ubuntu without installing, Install Ubuntu, Check Disk etc. If I select the live CD option the boot continues but the screen goes black with an error message Cannot display this video Mode.
I would have thought 18.04 would have supported a legacy graphics chip like the GMA 950 found in older systems.
For info the previous OS was windows 10 32 bit so there would have been a system partition as well as the main OS partition. The boot configuration would be legacy bios and not UEFI. 

Any help would be appreciated
Fozzie

---

### Post by Autodave on 2018-11-24
That is a rather old machine.  Exactly what version of ?buntu are you trying to install?  Have you added any memory to the rig?  (It only came with 1/2 gig of RAM.)  Are you trying to install 32 or 64 bit?

---

### Post by fozziebear on 2018-11-24
> **Autodave said:**
> That is a rather old machine.  Exactly what version of ?buntu are you trying to install?  Have you added any memory to the rig?  (It only came with 1/2 gig of RAM.)  Are you trying to install 32 or 64 bit?

Agreed its an old machine but that's why I am trying to install Xubuntu 18.04. I'm only using the machine in my garage to play back audio books and plays downloaded from the internet and copied to the pc across the network from my torrent PC also Xubuntu but 16.04. Its USFF so fits in a cupboard :-)

It has 2gb ram installed and 3.0 Ghz Pentium D processor. It happily runs windows 10 32bit but breaks every time there is a version update, hence my move to Linux. Xubuntu minimum spec is 512mb (ideal 1GB) ram 7.5Gb (ideal 20Gb) HDD space and processor that supports PAE. Whilst not generous in modern hardware I have double recommended ram and 80 Gb hard drive. 
I am trying to install the 32 bit version of 18.04
Fozzie

---

### Post by ajgreeny on 2018-11-24
It could be worth checking that your iso file used to create the install medium is good according to the hashes shown at [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes) and also perhaps trying Lubuntu 18.04 in place of Xubuntu; it uses even fewer resources than Xubuntu and may just run faster and better.
I am, however, surprised that Xubuntu is giving this problem as your spec ought to be OK for that version.

After booting to the black screen can you use Ctrl+Alt+F2 to get to a command line login, and there run ```
sudo apt install xserver-xorg-video-intel
```
That may say the latest version's already installed, and fine if so, but if it's not, the command will install it and could solve your problem, though I've no idea why it would not be installed by default.

---

### Post by fozziebear on 2018-11-24
Many thanks **ajgreeny** will try that. Also thanks for tip on Lubuntu. I have previously considered this but never actually tried it. Also considered Core version of Xubuntu as I dont use most of installed stuff except mousepad and Parole for playback.
Fozzie

---

