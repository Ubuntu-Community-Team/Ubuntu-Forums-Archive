---
title: "xcompmgr problems"
date: 2005-10-26
forum: Desktop Environments
---

### Post by jiggyup on 2005-10-26
hi, im trying to get transparent windows/fading to workon breezy 5.1, but i get this
```
           No Composite Extension

``` when i try to run something like
```
             xcompmgr -cfF

``` and i've already edited the end of xorg.conf to supposedly be enabling composite

this is what my xorg.conf device part looks like
```
 Section "Device"
    Identifier    "NVIDIA Corporation NV17 [Geforce4 MX 440]"
    Driver        "nv"
    BusID        "PCI:1:0:0" 
    Option         "RenderAccel"         "true"
    Option         "AllowGLXWithComposite" "true" 
EndSection
``` 
i've also tried using nvidia as a driver, but then xmanger doesn't seem to work

can anyone point out what i'm doing wrong, or the problem?

---

### Post by ltmon on 2005-10-26
Ok you should be using the nvidia driver, not nv else your performance will be pretty bad.

Next, yuo need this section in your /etc/X11/xorg.conf as well as what you already have:

Section "Extensions"
    Option "Composite" "true"
EndSection

Then you might have some luck

L.

---

### Post by jiggyup on 2005-10-26
the problem is, when i put "nvidia" as the driver it won't work for some reason, even though i have an nvidia card

also i do have
```
Section "Extensions"
     Option "Composite" "true"
EndSection
```
in my code, but i still get 
```
No composite extension
```
which is why i am confused

as a sidenote, i saw in a thread to try 
```
Section "Extensions"
     Option "Composite" "Enabled"
EndSection
```
which also didn't work

---

### Post by fannymites on 2005-10-26
Did you reboot after editing xorg,conf?  Not sure if you actually have to or not but I would imagine so.

---

### Post by Dr. Nick on 2005-10-27
Have you installed the restriced modules package to get the nvidia driver?

here is my relevant xorg.conf which works

```
Section "Extensions"
        Option  "Composite" "Enable"
EndSection

Section "Device"
        Identifier      "NVIDIA Corporation NV18GL [Quadro4 NVS AGP 8x]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "UseFBDev"              "true"
        Option          "RenderAccel"           "true"
        Option          "AllowGLXWithComposite" "true"
EndSection
```

---

### Post by jiggyup on 2005-10-27
actually i havent done that i mustve missed it

could you tell me how to go about doint it?

---

### Post by Dr. Nick on 2005-10-27
[QUOTE=jiggyup]actually i havent done that i mustve missed it

could you tell me how to go about doint it?[/QUOTE]


Open synaptic or use apt-get from the comand line and install the package nvidia-glx, If you are using synaptic It will tell you what to do after. Do that or just change xorg.conf to nvidia not nv and restart

---

