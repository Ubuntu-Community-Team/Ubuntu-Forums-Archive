---
title: "Installing a game"
date: 2006-11-06
forum: Gaming &amp; Leisure
---

### Post by thecynicality on 2006-11-06
I'm trying to install GRAW to see if it will work, i ran the first cd with wine and its going fine, but when it asks for cd2 and i put it in, it doesn't read it, i don't even thing ubuntu detects it. Can anybody help, or point me in the right direction?

---

### Post by Joe_CoT on 2006-11-06
Try remounting the cdrom drive
```
sudo umount /media/cdrom0
sudo mount /dev/hdc /media/cdrom0
```

The dev location of your cdrom drive might be different on your system. check your /etc/fstab to see where yours is

You might be better off making images of them. See this post [here](http://www.linuxforums.org/forum/wine/55951-wine-wont-give-me-cd-1-back-2.html)

---

