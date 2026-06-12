---
title: "boot loader order"
date: 2009-05-01
forum: General Help
---

### Post by kenmorgan01 on 2009-05-01
I'm extremely new to Ubuntu. I just need a way to have windows vista boot automatically instead of Ubuntu. I've done a fair amount of searching and just can't quite get ahold of it. can I use the Super Grub disk to do this?

---

### Post by taurus on 2009-05-01
You can either edit /boot/grub/menu.lst

```
gksudo gedit /boot/grub/menu.lst
```
and change the **default 0** to whichever entry for windows, start counting from 0.

Or you can install startupmanager and use it to configure your GRUB.

```
sudo apt-get update
sudo apt-get startupmanager
gksudo startupmanager
```

---

### Post by utnubuuser on 2009-05-01
There are several ways to approach the issue.  

Simplest?  Look in synaptic for "Startup Manager". This app/utility lets you customize grub etc, including selecting which OS is default.

Otherwise, you can edit /boot/grub/menu.lst

---

### Post by kenmorgan01 on 2009-05-01
thanks both of you for your quick response. the start up manager worked once I figured out how to find,install and launch it.
I appreciate you help.

---

