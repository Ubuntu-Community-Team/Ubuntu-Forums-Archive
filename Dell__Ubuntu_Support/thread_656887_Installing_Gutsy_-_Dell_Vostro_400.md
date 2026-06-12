---
title: "Installing Gutsy - Dell Vostro 400"
date: 2008-01-03
forum: Dell  Ubuntu Support
---

### Post by pdxkid on 2008-01-03
I ran into a number of issues install Ubuntu on a new Dell Vostro 400, namely, that neither the LiveCD nor the Alternate CD would boot.  Neither would Xubuntu or any other Ubuntu based distro although Gentoo based distros would boot (such as Sabayon).  

Removing the 'splash' and 'quiet' boot parms I was able to see it was hanging after initializing the CPU and, if I passed the noapic and noapci parameters it would hang an instant later on something else (looked like the first PCI device perhaps?).

Oh yea, by hang i mean a hard lock up..needed to hold down the power button to restart the PC.

Basically, there wasn't much info on the Vostro 400 since it is so new so I thought I would post this to help others since it was a headache for me and I *really* wanted to use my shiney fast new PC.

To get Ubuntu to boot, install, and continue booting after the installation you will want/need to do 2 things:
1) Update the BIOS  [I went from 1.04 to 1.08..then went on vacation for the holidays, came back, and 1.0.10 was out)

2) Change the USB controller in the BIOS to Normal/Slow (whatever the option that isn't FAST/HighSpeed is called...there are only 2 choices and actually very minimal settings you can change in the BIOS overall)

When the USB controller is set to the highest speed, it won't boot.

Evidently this is being fixed for the blah blah.24-2 Kernel in Hardy but I haven't tested Alpha2 (and updated the kernel) to verify.

Good luck everything and thanks to everyone who has given back to the community and helped folks like me!

---

### Post by kris1351 on 2008-02-13
I didn't have those issues. I just got one of these because they gave me a 22" flat screen with it and so far it is a nice machine. I have run Kubuntu and Ubuntu on it without issue with a default live cd install. The only issue I have run into is I added a second 500GB drive to it and at first it did not recognize 2 drives. I ran a Maxblast on both of them and then it came right up in the install.

---

