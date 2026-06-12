---
title: "How do I remove xwinwrap?!?"
date: 2009-08-30
forum: Desktop Environments
---

### Post by Cannon1230 on 2009-08-30
I installed the deb, extracted the sub file to my home folder, and followed terminal instructions. It would have worked, but evidently I have a crappy video card, and all the animations did was flicker.  I followed the code instructions to remove, but still do not have my icons or desktop background back. 
here is the code I used to try to remove it...
```
sudo apt-get remove xwinwrap
```

also I used this code to re-enable my desktop icons...
```
gconftool-2 -s '/apps/nautilus/preferences/show_desktop' --type bool true
```

I'm fairly new, so please forgive my stupidity! 
PLEASE HELP! Thanks,
Cannon

---

### Post by Cannon1230 on 2009-08-30
> **cannon1230 said:**
> i installed the deb, extracted the sub file to my home folder, and followed terminal instructions. It would have worked, but evidently i have a crappy video card, and all the animations did was flicker.  I followed the code instructions to remove, but still do not have my icons or desktop background back. 
Here is the code i used to try to remove it...
```
sudo apt-get remove xwinwrap
```

also i used this code to re-enable my desktop icons...
```
gconftool-2 -s '/apps/nautilus/preferences/show_desktop' --type bool true
```

i'm fairly new, so please forgive my stupidity! 
Please help! Thanks,
cannon
all i had to do was restart... Too much drugs as a kid

---

