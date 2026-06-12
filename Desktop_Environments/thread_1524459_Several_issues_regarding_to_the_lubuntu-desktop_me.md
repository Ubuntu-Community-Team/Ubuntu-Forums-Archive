---
title: "Several issues regarding to the lubuntu-desktop meta package"
date: 2010-07-05
forum: Desktop Environments
---

### Post by adudutz on 2010-07-05
Here's what I've done on my old P3 system (in order):

Installed Xubuntu 9.10 w/ LILO as the bootloader (GRUB2 doesn't work; the system cannot boot)
Replaced LILO w/ GRUB
Upgraded to Xubuntu 10.04 using the Alternative CD
Deleted the Xubuntu desktop using the command posted in Psychocats ([http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)) and replaced it with lubuntu-desktop meta package (replaced GDM w/ LXDM)
Added Lubuntu PPA repository
Replaced pcmanfm with pcmanfm2

Now, the problems:

1. The desktop is not drawn anymore (no shortcut icons), even when I tried to run pcmanfm -d from the terminal. Right-clicking the background (still drawn) will only show the Openbox menu
2. Every time I want to shutdown or reboot the PC, I have to log out first to the login screen and press 'Quit' button. I think it should be able to be done throught the Shutdown button instead.
3. The bootsplash simply doesn't work. It shows 'broken' display with overlapping texts instead of the Ubuntu/Lubuntu logo. This has been an old issue since I used the 9.10 (that time, only texts were displayed instead of Xfce logo)
4. Every time I shut down the PC, it doesn't turn off automatically (after 'shutting down' shows up, it freezes there). I have to turn it off manually by unplugging the power. Is it related to the Linux or the motherboard?

The system is equipped with an old ATI RAGE 3D AGP 8MB Graphics Adapter.

Any suggestions?

PS: the Yamaha PCI audio card attached to the PC is not detected.

---

