---
title: "Broken desktop after playing with compiz settings"
date: 2009-08-07
forum: Desktop Environments
---

### Post by narkie on 2009-08-07
Hi All,
I am new here and in need of some help. I was messing with what appeared to be simple display enhancements in a configuration menu within gnome last night. After making this change, everything: menu's, windows, panels, etc) went black as soon as what I assume is, they were re-drawn.

now, when I restart, gnome, I can login (display settings look fine), and then I am shown my panels, desktop wallpaper, (etc) but as soon as I open a directory on my desktop, goto the menu, these items are drawn in a dark shade of blank (black windows).

I had compiz working correctly for some time, however I now have no idea how to get things working again. 

I have tried logging in using a failsafe xterm session and accessing the compiz settings. I have disabled ALL options in ccsm I believe I was using simple-ccsm last night when I made the change that blew everything to bits. Currently in simple-ccsm the profile is set as "minimal". However, there may have been another configuration wizard I was using at the time.. any suggestions on what that might have been? 

At this stage, I would be happy to not use any desktop effects at all.

my xorg.conf file has very default/generic settings in it. These have worked for me well on my Intel945G card. (This is an older Samsung X60 laptop).

```

Section "Device"
Identifier "Configured Video Device"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection
```
 
The output of the LSPCI command is telling me I have an Intel Corporation Mobile 945GM/GMS, 943/940GML Express Intergrated Graphics Controler (rev 03)

the issue looks similar to this problem:
[http://www.linuxforums.org/forum/ubuntu-help/144562-progressive-black-screen-compiz-fusion-effects.html](http://www.linuxforums.org/forum/ubuntu-help/144562-progressive-black-screen-compiz-fusion-effects.html)

(edit) I can also see the configuration wizards if I open them when in failsafe xterm from the terminal (/edit)

If you have any ideas, please let me know.
Regards,
Matthew.

---

### Post by narkie on 2009-08-07
I have uninstalled compiz for now to workaround the issue. Will investigate what I did to cause this problem..

Will my compiz settings persist when I reinstall? Where does the configuration information live?

Regards,
Matthew.

---

### Post by drs305 on 2009-08-07
There is a .compiz folder in your home folder. I don't know what it contains but deleting it won't kill your system. I made a sample change and it was reflected in ~/.cache/compizconfig/

From the CCSM you can go to Preferences, Profile and there is an option to Reset to Defaults.

---

### Post by narkie on 2009-08-07
All is well now. I removed compiz with apt-get (specified the purge flag). I restarted then reinstalled compiz.

I was able to reproduce the issue that I had by turning on the effects -> blur setting in ccsm 

I have now made a backup of my compiz configuration.

Perhaps the compiz setting manager could display a "5 second settings change confirm" or something along those lines. 

Thanks for your assistance drs305.

Regards,
Matthew

---

### Post by Bearded-flower on 2009-08-08
> **narkie said:**
> All is well now. I removed compiz with apt-get (specified the purge flag). I restarted then reinstalled compiz.

I was able to reproduce the issue that I had by turning on the effects -> blur setting in ccsm 

I have now made a backup of my compiz configuration.

Perhaps the compiz setting manager could to a 5 second settings change confirm or something along those lines. 

Thanks for your assistance drs305.

Regards,
Matthew


I had the exact same problem a few months back, caused by blur aswell, exept i wasnt so lucky.

---

