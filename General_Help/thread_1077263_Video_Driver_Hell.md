---
title: "Video Driver Hell"
date: 2009-02-22
forum: General Help
---

### Post by spliffeh on 2009-02-22
I'm having one heck of a time getting Nvidia drivers working.  I've tried with envy, the package manager, and finally i've tried from nvidia's site.

I tried ENVY multiple times & with all three versons of the nvidia driver it lists: I uninstall current drivers, reboot, then go in and then install one... reboot... 

Each time before the login screen I get a popup message from Ubuntu.. but the font is so small I can't read it (????), I know it's about my video drivers though... it has three buttons at the bottom, I can't read what they say either.. I just click the right side one since that one lets me keep logging in, i've tried them all

I get into Ubuntu.. i'm at 640x480 or whatever... I go to System -> Administration -> Hardware Drivers, nothing is listed... it's clear that nothing installed.. argh

So plan B... I uninstall everything... go to Nvidia's website... grab the most recent 64bit linux drivers.. I go cntl-alt-f1, shut down GDM and sh the driver package. Somewhere along the line it gives me errors, something about kernel packages or something missing, then it tries to check nvidia's site for them and fails.

Any help would be appreciated 

- Geforce 7800 GTX
- AMD X2 4200 64bit
- Ubuntu 8.04 64bit

---

### Post by spliffeh on 2009-02-22
..I just tried again with package manager... got the unreadable popup again... no hardware drivers detected

i notice my xorg.conf doesn't list any video modes.. the drivers clearly aren't working even though package manage says their installed


:(

---

