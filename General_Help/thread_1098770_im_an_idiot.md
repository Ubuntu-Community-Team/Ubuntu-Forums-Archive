---
title: "im an idiot"
date: 2009-03-17
forum: General Help
---

### Post by hp owner on 2009-03-17
well i just reinstalled ubuntu and changed the screen resolution to the wrong setting, now i cant see a thing, my monitor has a green, red, and blue box that floats around saying "out of frequency range set resolution lower" is their any thing i can do without reinstalling??? 



thanks in advanced

---

### Post by kanikilu on 2009-03-17
Can you boot up in recovery mode and see if a backup of your xorg.conf file is in */etc/X11/*? If not, I think you'll need to either manually edit the xorg.conf file or run ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by D3ath on 2009-03-17
I would just edit the xorg.conf to your resolution thats what i did with my 32 inch LG 1080p and now it work wonderful!

---

