---
title: "Compiz Fusion on 1420N"
date: 2008-01-28
forum: Dell  Ubuntu Support
---

### Post by dhedrick on 2008-01-28
I have a feeling that I'm a complete idiot here, but I'm hoping that someone can help me...

I'm completely new to Linux, and just purchased a Dell 1420N preinstalled with Ubuntu 7.10.  I would like to run the Compiz Fusion desktop effects, but can't figure out for the life of me how to go about doing that.  Can anyone give me some idea?  It seems like this should probably be easy since Synaptic already shows the packages installed, but I can't find anything anywhere on how to activate them...

Thanks!

~ Dale

---

### Post by prankst3r on 2008-01-28
Hi Dale,

You probably do not have the Compiz Settings Manager installed:

```
sudo apt-get install compizconfig-settings-manager
```

After you've installed that, go to System->Preferences->Advanced Desktop Effects Settings.

---

### Post by jsonder on 2008-01-28
If you right click on the window, you will bring up a window with "Appearance Preferences".  If you left click on the "Visual Effects" tab (last one on right) and select the maximum option at the bottom, you should get what your video card can yield.

Shoot, I don't go for bling so I hope that this works for you.

---

### Post by magicliu on 2008-01-29
As you mentioned above, i am sure, dell has configured all drivers and programs  for you already, so just right click the desktop, Appearance Preferences, left click the visual effect, see if you can custom it :D or
System->Preferences->Advanced Desktop Effects Settings.


if u don't have:( too bad. u need to install it~ see prankst3r's post~~~ but make sure the graphic card driver works fine~~~


sorry for my poor english~:D cheer~

---

### Post by notwen on 2008-01-29
Depending on which graphics chipset you choose for your Inspiron1420n, the Intel X3100 or Nivida, the Intel X3100 chipset(currently blacklisted) will not work w/ Compiz-Fusion until you adjust some settings.  See [here]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Compiz_Fusion_965GM_Incompatibility") for the workaround.  From what I understand this may/may not interfere w/ video playback while Compiz-Fusion is enabled.  Hope this helps. =]

---

