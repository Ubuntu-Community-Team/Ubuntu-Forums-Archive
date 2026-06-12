---
title: "Problems starting Screens and Graphics"
date: 2008-01-11
forum: Desktop Environments
---

### Post by niels on 2008-01-11
I have some problems starting Screens and Graphics. When I try to start it from a teminal, I get the following errors:

```
mads@mads:~$ sudo displayconfig-gtk 
[]
Traceback (most recent call last):
  File "/usr/bin/displayconfig-gtk", line 75, in <module>
    app = DisplayConfig(options)
  File "/usr/lib/python2.5/site-packages/displayconfiggtk/DisplayConfig.py", line 190, in __init__
    debug_scan_pci_filename=self.options.pcitable)
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 392, in __init__
    self._finalizeInit()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 411, in _finalizeInit
    self.setLayout(gfxcard._getDetectedLayout())
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 965, in setLayout
    gfxcard.setLayout(XSetup.LAYOUT_CLONE)
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1177, in setLayout
    screen._resyncResolution()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1854, in _resyncResolution
    self.gfx_card.setup.getPrimaryScreen()._resyncResolution()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1810, in _resyncResolution
    (preferred_width,preferred_height) = self.getAvailableResolutions()[-1]
IndexError: list index out of range
```

Does anyone know what's wrong?

---

### Post by Elliot.strumlauf on 2008-01-12
Same problem with me. I am running an HP laptop with graphics, no problems, and compiz and emerald are working fine. I assume, then, that my graphics card is also fine. Now, my laptop screen is 1280x800, works fine, but I have a 22inch LCD flat panel that I use and want to get it working. I opened up graphics and screen EARLIER, and set up my monitor as a generic 1680x1050 (windows max resolution, what I want). So, like an idiot, forgetting how easily it could backfire, I set the LCD as my default monitor. I get 1440x1050 right now, the only higher setting is like 1730x1330 or something too large. So, here I am, unable to open "Screen and Graphics", working with an out of resolution LCD monitor, and cannot switch back to my laptop (so it is worthless on the road). Yikes.

When I type in sudo displayconfig-gtk I get the same error as him.

---

### Post by Elliot.strumlauf on 2008-01-14
Any help would be nice...

---

### Post by Echelon VI on 2008-01-19
I have the same problem :S Please somebody help!

---

### Post by GiraffeNecktie on 2008-01-28
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/displayconfig-gtk/+bug/128994](https://bugs.launchpad.net/ubuntu/+source/displayconfig-gtk/+bug/128994) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have the same problem on my HP TX1000 with Nvidia video. Sounds like it might be the same as this bug: [https://bugs.launchpad.net/ubuntu/+source/displayconfig-gtk/+bug/128994](https://bugs.launchpad.net/ubuntu/+source/displayconfig-gtk/+bug/128994)

---

### Post by Elliot.strumlauf on 2008-01-28
I found a weird solution to set up an external monitor with an HP laptop (bypassing screen and graphics).



 Uninstall the Nvidia driver, reboot. Then install the driver with ENVY (google it). Reboot, and it'll give you a glitchy screen where the "New restriced Drivers in Use" should be (itll be blank), and double click it and enable the graphics driver. Reboot. Then, to edit anything with resolution or multiple screen, go under apps>system tools>Nvidia Settings.

---

### Post by Echelon VI on 2008-01-28
I finally found a solution. Run the following command in a terminal: sudo dpkg-reconfigure xserver-xorg

Be aware that there are a lot of options, but most of them are logical. Select the appropriate options and then whoopsy, screens and graphics now work again - hurray!

Your WELCOME! :D

---

### Post by Huss on 2008-01-29
Ah great! Thank you.


Now, if I try and set up a second screen again will it go through the same ordeal?

---

### Post by Echelon VI on 2008-01-29
Unfortunately yes, i just tried it, and the exact same thing happened. There seems to be a bug, so for now, don't mess around with two screens!

---

