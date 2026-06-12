---
title: "Desktops for 11.04"
date: 2011-05-02
forum: Desktop Environments
---

### Post by wildmanne39 on 2011-05-02
Hi, can anyone tell me if the desktop xfce can be installed at the same time as unity, I know that gnome 3 can not but I do not know about xfce desktop, because I would like to try another desktop but I do not want to break unity. Thanks for any help in this matter.

---

### Post by werewolves on 2011-05-02
I'm pretty sure you can just install "Xfce4" from the Ubuntu Software center, but I'm not home to try it.

I don't see why it would interfere with Unity at all.

---

### Post by Krytarik on 2011-05-02
XFCE's apps -namely Thunar- *can* indeed interfere with Unity (and possibly with any other DE) if you set them as the default applications for certain file types, and you remove just the app itself, but keep XFCE installed:
[http://ubuntuforums.org/showthread.php?t=1747534](http://ubuntuforums.org/showthread.php?t=1747534)

But if you don't do that, you're fine.
So, just go ahead and try XFCE!

To install:
```
sudo apt-get install xfce4
```To remove again:
```
sudo apt-get purge xfce4
sudo apt-get autoremove

```Greetings.

---

### Post by russ553 on 2011-05-02
I've tried Unity, Xfce, Gnome2 and LXDE with Natty and I prefer LXDE.

---

### Post by wildmanne39 on 2011-05-02
Thank you all for your help, I think I will install xfce after I backup my home folder, thanks again, I appreciate the help.:)

---

