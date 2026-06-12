---
title: "Please help me, I'm trap in the Windows OS"
date: 2006-09-26
forum: Desktop Environments
---

### Post by milagre23 on 2006-09-26
I've just follow a hint in a post to set a wacm tablet pen changing xorg by gedit and now I can't open my UBUNTU. A message appears telling me that there's a problem with the X system and it's only possible to open in text mode (which I can't operate).

Please help me, I'm trap in the Windows OS.

---

### Post by Dinerty on 2006-09-26
```
sudo dpkg-reconfigure xserver-xorg
```

this will allow you to set up xorg again, be careful though.

Did you make a backup of xorg.conf?

---

### Post by Kateikyoushi on 2006-09-26
What did you change ?
Did you modify your /etc/X11/xorg.conf file ?

---

### Post by bulldog on 2006-09-26
Hope you made a copy of your xorg.conf before you altered it?

If so put the copy back.

```
sudo cp /etc/X11/xorg.conf-backup? /etc/X11/xorg.conf 
```

If not you could try to reconfigure your X-server

```
 sudo dpkg-reconfigure -phigh  xserver-xorg 
```

Then restart gdm

```
/etc/init.d/gdm restart 
```

---

### Post by Dinerty on 2006-09-26
If you still feel nervous try:

[http://ubuntuforums.org/showthread.php?t=258186](http://ubuntuforums.org/showthread.php?t=258186)

---

### Post by milagre23 on 2006-09-26
Thank you all for your quick answers. I think I changed all dev/wacom for dev/(something I can't remember)/wacom - Anyway I think I can remeber if I see it. I'll try your advise and then I report.

Thanks again

---

### Post by milagre23 on 2006-09-26
Thank you all, guys. Im back in my good old UBUNTU!

---

