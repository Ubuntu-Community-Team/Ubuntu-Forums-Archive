---
title: "Installed LXDE from source, font looks bad in firefox."
date: 2009-03-12
forum: General Help
---

### Post by Neo_The_User on 2009-03-12
I compiled and installed LXDE from source using the Ubuntu minimal install, expert command line install. I edit xinitrc, rc.conf and all that to my liking and reboot. LXDE starts by itself on startup, I launch firefox and all the fonts in firefox look pixelated sort of. I can read it just fine but its not as good as when I used to run GNOME 2.26. Any suggestions?

---

### Post by spcwingo on 2009-03-12
You might want to try other fonts.  Try the MS core fonts.

```
sudo apt-get install msttcorefonts
```

---

### Post by Neo_The_User on 2009-03-12
> **spcwingo said:**
> You might want to try other fonts.  Try the MS core fonts.

```
sudo apt-get install msttcorefonts
```

Thanks. I only had ttf-bitstream-vera and dejavu. This works. Thanks a ton!

---

