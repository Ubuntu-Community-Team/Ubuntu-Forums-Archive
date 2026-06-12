---
title: "Black screen on boot (9.04)"
date: 2009-06-06
forum: General Help
---

### Post by r0ji on 2009-06-06
Hello, I did a lot of searching for this problem and nothing has worked so far.

Yesterday, after having installed a couple of packages (including the suspect: the ATI Catalyst control center), Ubuntu booted up on a black screen with faint streaks of colour (faulty display). Two seconds pass, then the screen goes completely black. Another two seconds pass, and it becomes a lighter black with more streaks of colour. Repeating forever. I am forced to hard reboot, and only my WinXP is useable.

Other threads suggested changing drivers with dpkg-reconfigure xserver-org (from recovery mode command line, which I can access), but the utility only sets up the keyboard, and then dumps me back to the command line without mentioning anything about monitor or video.

I really thought the Catalyst control center had wrecked something, so at the command line I typed "sudo apt-get remove fglrx-control", the package is now gone but nothing has changed.

I also restored my xorg.conf to a previous version (one week old), but again nothing changed.

Please advise, I'm completely out of luck.
Many thanks in advance.

Edit: The computer is a Dell Inspiron 6400 with an ATI Mobility Radeon X1400 256MB, PCI-Express 16X.

---

### Post by Legace on 2009-06-06
Reboot PC, select "Recovery mode" in boot-manager (GRUB) and then go for "root shell" option (you might need to press the DOWN arrow a couple of times). 
After that just type:
```
sudo apt-get remove xorg-driver-fglrx
```

Now you will need to restore your original settings, so either restore any backed-up copy of file /etc/X11/xorg.conf or run something like:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

or another one (you will have to answer a few simple questions)
```
sudo dpkg-reconfigure xserver-xorg
```

then type
```
exit
```

and select "resume normal boot"

This should get you back to your Ubuntu desktop, but running on default drivers.

---

### Post by r0ji on 2009-06-06
Thank you, Legace! You're a hero. That worked perfectly.
I'll be sure to remember the trick.

Thanks again. Cheers!

---

