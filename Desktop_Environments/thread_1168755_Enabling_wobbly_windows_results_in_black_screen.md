---
title: "Enabling wobbly windows results in black screen"
date: 2009-05-24
forum: Desktop Environments
---

### Post by runekruse on 2009-05-24
Hi My Kubuntu installation crack when I try to enable wobbly windows. The screen becomes black, and when I restart the computer the log-in page is as usual, but after login the black screen returns. 
I can live without the wobbly windows, but can anyone help me get rid of the black screen. I have a feeling that Kubuntu is working underneath the black screen, but I´m not sure.

I´m new to Linux so please be gentle:-)

---

### Post by ckonestroh on 2009-05-24
TRY ALT + F2 THEN TYPE STARTKDE....

You may not be able to see what you type so look at hands to make sure your entering right keys....

But I do expect its your graphics card not being supported...


good luck

---

### Post by benerivo on 2009-05-24
Try Alt+F2 to get to a command line. Then log in, and type...```
nano ~/.kde4/share/config/kwinrc
```Then use the cursror to move to the section entitled [Plugins] and change the line that reads...```
kwin4_effect_wobblywindowsEnabled=true
```to...```
kwin4_effect_wobblywindowsEnabled=false
```Then hold Crtl and press X. Press y to save, then press Enter to confirm. Then Ctrl+Alt+Del to reboot.

---

