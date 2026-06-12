---
title: "Needed: How-To for installing new graphics card"
date: 2005-11-17
forum: Desktop Environments
---

### Post by MButterman on 2005-11-17
I had posted previously on the S3 Unichrome onboard graphics I have in my Biostar P4M80-M7. I finally found a Diamond Stealth II PCI graphics card. While this is only temporary until I get a newer card. How would I install this in Breezy? The card itself is alright but when installed, it causes a problem when attempting to boot to GUI so I only get text. I tried "sudo dpkg-reconfigure xserver.org" and it returns that no such command exist and that this package is not installed. I need instuctions to configure this card. thanks for the help.

AMB,
MButterman

---

### Post by RAOF on 2005-11-17
The command you're actually after is:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by MButterman on 2005-11-17
Thanks for the info, card is in and working. I figure anything is better than trying to get the onboard graphics to work right. Haven't checked the 3-D excelleration on it yet but I don't think there will be any problem.

AMB,
MButterman

---

