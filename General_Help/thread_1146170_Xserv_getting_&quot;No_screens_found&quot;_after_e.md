---
title: "Xserv getting &quot;No screens found&quot; after enabling NVIDIA drivers."
date: 2009-05-02
forum: General Help
---

### Post by Killers2 on 2009-05-02
Well I have 2 graphics cards that have 2 GPU's each (so 4 in total) and before I enabled them it was fine.

Running 9.04 I have reinstalled and tried several methods that I have found through searching.

I would appreciate it if someone could point me in the right direction :)

Thanks.
:popcorn:

PS my graphics cards are 9800gx2's and I am using the 64 bit version of Ubuntu.

**FIXED**
I added my BusID to the device section of my Xorg.conf and then did startx and then removed the drives from the hardware drivers thing then installed again and edited the Xorg.conf again BEFORE rebooting to add my BusID again.

---

### Post by Killers2 on 2009-05-02
Anybody?

---

### Post by Killers2 on 2009-05-02
Well I think I found out why it is doing it. It does not appear to be setting a primary device and detects 2. Anyway to tell it which to use?

---

### Post by LinuxGuy1234 on 2009-05-02
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Killers2 on 2009-05-02
> **LinuxGuy1234 said:**
> ```
sudo dpkg-reconfigure xserver-xorg
```
Still not finding any screens.

---

### Post by Killers2 on 2009-05-02
Fixed.

PS you can get your BusID by doing

sudo nano DIRECTORYTOXORGLOGHERE and browse through it.

---

