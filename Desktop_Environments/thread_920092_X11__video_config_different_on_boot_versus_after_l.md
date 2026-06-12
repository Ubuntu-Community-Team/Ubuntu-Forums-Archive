---
title: "X11  video config different on boot versus after logout"
date: 2008-09-14
forum: Desktop Environments
---

### Post by mubun on 2008-09-14
I've setup my xorg.conf (and nvidia settings) to properly utilize my four monitors running on an Nvidia Quadro NVS440.

When X is run for the first time after a system reboot, the configuration isn't correct - one of the four displays doesn't receive signal at all and the remaining three screens aren't configured as xorg.conf says they should be (i.e. two screens are receiving the same signal, etc.).

If I logout, then log back in (same user) the correct configuration is used and all four monitors work perfectly.
 
Can anyone suggest a reason why the correct configuration is not used at the first login?  Thanks.

---

### Post by Reilithion on 2008-11-08
I have exactly the opposite problem.  After I first boot up, my display is detected and used correctly.  But after I log out, the graphical interface vanishes and refuses to come back.  I have gone to the console to check things out and here's what I've found:
- The /var/log/Xorg.0.log file displays completely different stuff after logging out than it did the first time Xorg ran.  After logging out, it fails out saying that the VESA module could not detect a display.
- After failing to restart Xorg the first time, gdm tries to run Xorg with failsafe settings found in /etc/X11/xorg.conf.failsafe and gets the same error about VESA.
- The first time Xorg is run, it seems to have no trouble from VESA.  I don't see it loading the vesa module, but there are references to VESA gathering video modes.
- Even if I remove Load "vesa" from the /etc/X11/xorg.conf(.failsafe) files, the vesa module still tries to load and still fails to detect my display.
- sudo /etc/init.d/gdm restart does not solve the problem.

These may not be applicable to the problem you've been having, mubun, but the underlying issue does seem to be that something -- either gdm or Xorg -- is behaving differently between first login and after first logout.

---

### Post by Athanis on 2008-11-24
I have a similar problem. I cannot get X to start with my NVS440 (ubuntu 8.10, 64 bits). Does any of you found a solution to the problem?
Edit to add: Fixed the problem, i just have to add the
BusID "PCI: ?? : ?? : ??", where ?? : ?? : ?? is the PCI bus addres of your card (you get it with 
lspci | grep -i nvidia )
to the xorg.conf file in the Device section.

---

### Post by mubun on 2009-01-03
Not a solution for me unfortunately, my xorg.conf already has BusID settings that match what is dumped by lspci:

```

~$ lspci | grep -i nvidia
01:00.0 PCI bridge: nVidia Corporation Unknown device 01b3 (rev a3)
02:00.0 PCI bridge: nVidia Corporation Unknown device 01b3 (rev a3)
02:01.0 PCI bridge: nVidia Corporation Unknown device 01b3 (rev a3)
03:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 440 (rev a2)
04:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 440 (rev a2)

```

```

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 440"
    BusID          "PCI:3:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 440"
    BusID          "PCI:3:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Videocard2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 440"
    BusID          "PCI:4:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard3"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro NVS 440"
    BusID          "PCI:4:0:0"
    Screen          1
EndSection

```

---

### Post by hinge on 2009-03-02
Hi,

I have the same problem. My system boots fine and X/GDM loads without problems. If I try to logout, do a ctrl-alt-backspace my gdm will not restart. It tries again and again until I give it the knife. There are no errors in my xorg log.

Did any of you find a solution?

I have a T61p with a nVidia Corporation Quadro FX 570M (rev a1)...

---

### Post by yield999 on 2009-03-02
I have a similar problem. I use the ATI Catalys controll center to change my video card setting to work with my dual display setup.

It look like the setting has been changed and asking me to reboot.
I reboot the I get the splash screen to log on, I immediatly see that the dual display is working fine, but AS SOON I LOG IN, the dual display goes back to "clone" mode instead of 2 "different" display that I can drag and drop windows at....

Any ideas what we could do to fix the problem...
Please help, this really is a PITA.... :(

---

