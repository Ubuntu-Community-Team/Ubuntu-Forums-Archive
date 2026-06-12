---
title: "nvidia problem?"
date: 2005-11-29
forum: Desktop Environments
---

### Post by micder on 2005-11-29
Hello everybody,

Just installed Ubuntu and I'm surprised how well all went.
A real nice desktop and my onboard NIC (sk98lin) was detected.
New updates were installed and all went fine, until I came back to my computer after lunch. Screen was black and did not react on mouse or keyboard.
Ctrl+Alt+Del and restart went well until the GUI should come up:
Again a black screen.
Possible causes:?
1. Did the update screwup my X; I recall some X files from the update passing by.
2. Is the nv driver the problem?

```
Section "Device"
        Identifier      "NVIDIA Corporation NV40 [GeForce 6200 TurboCache]"
        Driver          "nv"
        BusID           "PCI:4:0:0"
EndSection

Section "Monitor"
        Identifier      "E-191"
        Option          "DPMS"
EndSection
```

The Monitor is an Neovo LCD: detection seems OK

Any help is much appreciated

---

### Post by Ampersand on 2005-11-29
Try pressing "Ctrl, Alt and F2" to get to a terminal. Login here and type
```
sudo /etc/init.d/gdm restart
```

and see what the error message is.

Generally,problems like these can be solved by running
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by frodon on 2005-11-29
You could first try that in a virtual terminal (Ctrl+Alt+F1) : ```
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
```And then reboot.
Also it's always a good idea to put in your xorg.conf your refresh rate parameters. So give us the full name of your screen or the Horizontal and vertical refresh rates value of your screen and we will tell you how modify your xorg.conf

---

### Post by micder on 2005-11-29
Thank you Ampersand: that's fast!

I'm back in Ubuntu:
Changed the driver in xorg.conf to vesa.

BTW: Ctrl+Alt+F1 did not work when the screen was frozen

In Slack the following works OK:
HorizSync   24.0 - 80.0
VertRefresh 49.0 -75.0
driver nvidia

Don't see HorizSync and VertRefresh in my xorg.conf
The only change I made was vesa i.s.o nv

Can I sudo dpkg-reconfigure xserver-xorg, while in X?

---

### Post by micder on 2005-11-30
Inserted HorizSync and VertRefresh in my xorg.conf.
Further followed instructions to install nvidia driver 
per: [http://doc.gwos.org/index.php/Install_Nvidia_driver]("http://doc.gwos.org/index.php/Install_Nvidia_driver")
Thanks guys

---

