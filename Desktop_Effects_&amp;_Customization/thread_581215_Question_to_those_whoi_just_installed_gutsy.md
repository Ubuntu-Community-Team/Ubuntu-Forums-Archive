---
title: "Question to those whoi just installed gutsy"
date: 2007-10-19
forum: Desktop Effects &amp; Customization
---

### Post by ehdtkqorl123 on 2007-10-19
After installing gusty, if you enable the desktop effec, compiz-fusion seems to work. If I press ctrl+alt+arrpow then the screen moves in a plain. How can I change this to cube? I couldn't find any manager there. I tried to do

sudo apt-get install ccms, it didnt work.
Any tips?

---

### Post by Lavos on 2007-10-19
Try the command ```
sudo apt-get install compizconfig-settings-manager
``` to install the manager. Or you can use the Synaptic Package Manager; do a search for compiz there and you should find it.

After the install you should find the manager at  System>Preferences>Advanced Desktop Effects Settings  , you need to enable the Desktop Cube there.

---

### Post by ehdtkqorl123 on 2007-10-19
Yea I did that on Gutsy, but is not working. I think it is repository issue...

---

### Post by cro_crx on 2007-10-19
Yeah it sounds like it, just head over to System --> Administration --> Software Sources, and you can tick the boxes for the sources you want. not 100% sure which one you need though ,just tick em all :P

---

### Post by AlanR8 on 2007-10-19
You need to go into the general options of the CompizConfig Manager and hit the Desktop Size tab. Next change the Horizontal Virtual size to 4. It defaulted to 1 on my installation. (Kubuntu). You should then have a cube! Enjoy :guitar:

---

### Post by ehdtkqorl123 on 2007-10-19
how can I access that general option? which menu? I will be grateful if you let me know that process.. even though it sounds simple, that's what I have been struggling with these days..

---

### Post by AlanR8 on 2007-10-19
Click on the "General Options" as below when it's highlighted. The options then open up!

---

### Post by ehdtkqorl123 on 2007-10-19
Ahh is that Gutsy Gibbon? If so, when you installed compizconfig setting manager, did you just use 

sudo apt-get install compizconfig-setting-manager?

Since gusty contains compiz-fusion, I can see some effects, but it doesn't contain the setting manager..so I wanted to install it but couldn't,,,

---

### Post by cymrujmc on 2007-10-19
The easiest way I found was to go to Add/Remove programs, show "all available applications" on top right corner, search ccsm or compiz, and it shows right up.  Good luck.

---

