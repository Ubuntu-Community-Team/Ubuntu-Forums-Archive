---
title: "Some non-gnome apps have ugly fonts"
date: 2005-07-10
forum: Desktop Environments
---

### Post by balazs on 2005-07-10
Hi guys,

I have used the "Front Preferences" to setup the look of gnome. When i start some programs however it seems that they do not use this settings, and they have a really ugly look (huge font size, unknown font type)

3 examples:

If i right click on XMMS to change settings
Skype overall look
GNU Cash overall look

I am a newbie, so i am just guessing. Is this because this programs get their font settings from xorg not gnome, and my xorg settings are not proper?

Where can i set this properly?


Thanx,


Balazs

---

### Post by Dasch on 2005-07-10
I just corrected this. Check this link out. I set the size to 150 in /etc/gtk/gtkrc.utf-8.
[http://www.ubuntuforums.org/showthread.php?t=46347](http://www.ubuntuforums.org/showthread.php?t=46347)

---

### Post by balazs on 2005-07-10
Thanx for the answer.


I have tried what u have suggested, and set the value to 150, but nothing has changed. Maybe i have to modify another setting, not the utf-8. I am just guessing.
I will play around the files, maybe i will find the correct setting.

By the way, what does 150 stand for? Why that much?


Balazs

---

### Post by angkor on 2005-07-10
Give this a try to improve the look of skype and other qt apps:

```
 apt-cache search qt | grep config
qt3-qtconfig - The Qt3 Configuration Application
```

---

### Post by balazs on 2005-07-10
Success!

I followed once more the links, and found one topic in the Ubuntu wiki. I just had to create the gtkrc.mine file, and everything works fine now.


Thanx,


Balazs

---

