---
title: "screen tearing with compiz + ati 5850"
date: 2010-02-22
forum: Desktop Environments
---

### Post by gonintendo on 2010-02-22
im using compiz with the 10.1 ati drivers and i get really bad tearing. it seems to be pretty common, but i haven't found a fix. can anyone help? i have tried sync to vblank and disabling the refresh rate detection. thanks!

---

### Post by byStanderone on 2010-02-22
...hope this bit of info would help, tearing is more on the horizontal sync functionality, try to findout the horizontal range setting in your xorg.conf and compare it with your display specs, edit xorg.conf if necessary. (or perhaps this may be a display software issue)

---

### Post by gonintendo on 2010-02-23
and where might i find the xorg.conf? sorry, im a noob at linux.

---

### Post by gonintendo on 2010-02-23
ok, nvm, i just searched for it. all it contains is
> Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

---

### Post by byStanderone on 2010-02-23
...more of a driver issue, perhaps you've seen this:
[http://ubuntuforums.org/showthread.php?t=1389889&highlight=ati+5850](http://ubuntuforums.org/showthread.php?t=1389889&highlight=ati+5850)

---

### Post by tdr2009 on 2011-03-06
This worked for me. 

Go to System > Preferences > ATI Catalyst Control Center (Administrative)

When it opens, go to More Settings under 3D.
Then under "Wait for Vertical Refresh" move slider to Always On. 

And don't worry, the screen will flicker some, but then it should fix screen tearing issues. It did for me. 

Hope I helped.

---

### Post by tdr2009 on 2011-03-06
Huh, so far, everytime you restart, you have to turn it off, then turn it on, just for it to work again. After I restarted after figuring this out, it started screen tearing again, with the option on. I went and turned it off and apply and it still screen teared. So i turned it on again, and it stopped screen tearing.

---

