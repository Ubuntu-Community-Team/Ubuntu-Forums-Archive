---
title: "Try to mix onboard and pci-e gfx. can't log in."
date: 2014-09-25
forum: Desktop Environments
---

### Post by Azyx on 2014-09-25
Hey.

I have a motherboard with an onboard nvidia:

00:05.0 VGA compatible controller: NVIDIA Corporation C51 [GeForce 6150 LE] (rev a2)

and a PCIe

03:00.0 VGA compatible controller: NVIDIA Corporation G84 [GeForce 8600 GT] (rev a1)

Using the propretarian Nvidia-drivers

During installation of Ubuntu 14.04, I turned off the onboard Geforce 6150 card. I turned it on now, and connected a display to the onboard vga-port, but when I came to the login, screen, I can not log in.  I thought it maybe was because the drivers for the onboard  Geforce 6150, never had being installed.

My need of the onboard gfx is not so important, so I change back in BIOS to only have singel vga and to first choose PCIe, as it was during installation. But now there is the same problem, I'm not able to log in. Coming back to the login screen again, and again and again....

However, I'm able to login true ssh, so I may run comands from there.

Any way I can fix xorg-config ore something... reconigure or so... Have not need to do it for a long time, and I don't know  if the old way, still works on Ubuntu 14.04...

Cheers

---

### Post by Azyx on 2014-09-26
Additional information.
I am also able to log into Guest-session, no password. 
And I can log in true ssh into my user acount, so I have not forget my password. 

If I use wrong password when I log in to my account from the computer, it come a small text, who says invalid password. If I type the correct password, the sceen went black for a while, the back to login screen, with no information....

---

### Post by Azyx on 2014-09-26
My .Xauthority file in /home/ have changed  owner and group to root. How is it possible????

Find that other have had that problem, so cheched and fixed  true ssh.

---

