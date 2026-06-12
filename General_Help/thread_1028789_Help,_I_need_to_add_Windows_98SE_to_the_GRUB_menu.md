---
title: "Help, I need to add Windows 98SE to the GRUB menu"
date: 2009-01-02
forum: General Help
---

### Post by Mulenmar on 2009-01-02
How do I do this? This is my friend's mother's computer, and she wants access to Windows 98SE as well as Linux.  The Ubuntu Server setup didn't detect Windows, and grub-update didn't do it. Windows is on (sd0,0).

---

### Post by Mulenmar on 2009-01-02
Emergency bump here, folks.

---

### Post by caljohnsmith on 2009-01-02
How about using:
```
title Windows 98SE
root (hd0,0)
chainloader +1
```
If that doesn't work, then change the (hd0,0), given that:
```
(hd0,0) = sda1
(hd0,1) = sda2
(hd0,2) = sda3
...etc
```
Assuming you have Grub installed to the MBR of the same drive that Windows is on. How about giving that a shot and let me know how it goes.

---

### Post by albinootje on 2009-01-02
> **Mulenmar said:**
> How do I do this? This is my friend's mother's computer, and she wants access to Windows 98SE as well as Linux.  The Ubuntu Server setup didn't detect Windows, and grub-update didn't do it. Windows is on (sd0,0).

Grub on Ubuntu already has an example for that :

try :
sudo gedit /boot/grub/menu.lst

```

# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1

```

It assumes that MS-Windows is installed on the first partition of the first disk. 
Is that correct for your situation ?
If so, simply uncomment those lines of the example, and edit them, that it looks like this :
```

title         Windows 98SE
root          (sd0,0)
makeactive
chainloader   +1

```
Then save and exit, and reboot to test it.

---

