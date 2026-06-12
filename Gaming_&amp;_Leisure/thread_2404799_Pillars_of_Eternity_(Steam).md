---
title: "Pillars of Eternity (Steam)"
date: 2018-10-28
forum: Gaming &amp; Leisure
---

### Post by caskin on 2018-10-28
Pillars of Eternity does not load at all running Ubuntu or Peppermint but runs fine on Manjaro. Using same computer, same Nvidia 390 drivers on a fresh install of Manjaro game runs great. Same thing on Ubuntu 18.10 and game does not load.  Anyone have any insight as to why this is?

Thanks

---

### Post by oldrocker99 on 2018-10-29
I've been using Ubuntu MATE as long as it's been available, and PoE, and for that matter, every other game I have bought on Steam, and that's a lot of games, has run just fine. Straight Ubuntu is pretty heavyweight. Please post the results of```
lspci
```

---

### Post by caskin on 2018-10-29
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C216 Chipset Family MEI Controller #1 (rev 04)
00:16.3 Serial controller: Intel Corporation 7 Series/C210 Series Chipset Family KT Controller (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (Lewisville) (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C216 Chipset Family High Definition Audio Controller (rev 04)
00:1d.0 USB controller: Intel Corporation 7 Series/C216 Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a4)
00:1f.0 ISA bridge: Intel Corporation Q75 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series/C210 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C216 Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GK208B [GeForce GT 710] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GK208 HDMI/DP Audio Controller (rev a1)

---

### Post by oldrocker99 on 2018-10-29
I personally don't see a reason why PoE shouldn't run. Try deinstalling the game, then reinstall it. Also, you can let Steam verify the files from the Properties and Local Files tab.

---

### Post by caskin on 2018-11-09
I have uninstalled steam, verified files, checked permissions, reinstalled game and other things but same result. For fun I installed OpenSuse and had no issues with the game as well. My Steam folder is on a separate drive so the files are not changed, Manjaro and Opensuse have no problems so I'm at a loss. Thanks for response though.

---

### Post by oldrocker99 on 2018-11-09
Of course, any distro you want is freely available, and if OpenSuSE does the job, terrific!

---

### Post by caskin on 2018-11-09
I honestly don't want to switch, Ubuntu seems to be doing everything else better than the rest. All of my apps work the way they should on Ubuntu vs many broken apps using Opensuse or Manjaro. I just don't play many games and POE is the one I play most so was hoping for some help tracking down the problem. Considering Peppermint 9 and Ubuntu 18.10 both have the same issue that two other completely different distros don't have I thought the comparison might help narrow it down. Appreciate the feedback though.

---

### Post by oldrocker99 on 2018-11-10
Try this:
```
sudo apt install mate-desktop-environment
```

Log out and log back in, selecting MATE as the desktop. It's lighter-weight than the default Ubuntu desktop, and extremely configurable. It can look like Windows (Redmond), Mac (Cupertino), and Unity (Mutiny). The default is a much-improved version of the desktop I fell in love with in 2008, GNOME 2.3. It is far, far advanced over GNOME 2.3. You can always delete it, but you just might like it.

---

### Post by caskin on 2018-11-11
Out of desperation I wiped the drive and reinstalled fresh. As of now everything works including POE. Still wish I knew what caused the problem but I'll take it. Thanks again. Problem solved.

Actually the entire problem was the fault of Private Internet Access application. Shutting it down completely resolves any issues with steam game play.

---

