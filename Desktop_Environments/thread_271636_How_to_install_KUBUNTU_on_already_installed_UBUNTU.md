---
title: "How to install KUBUNTU on already installed UBUNTU"
date: 2006-10-05
forum: Desktop Environments
---

### Post by umairsaeed219 on 2006-10-05
I want o install Kubuntu on laready installed ubuntu(6.06).
Is there any way that i can install it without removing Ubuntu so that later on i may switch to ubuntu
Thanks

---

### Post by meng on 2006-10-05
Sure, drop to a command line and type:
sudo aptitude install kubuntu-desktop

---

### Post by aysiu on 2006-10-05
It's probably not a terrible idea to update first: ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
``` Full instructions here:
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

### Post by umairsaeed219 on 2006-10-05
Actually i want to update it using KUBUNTU cd not internet because i have dial up.
and method above advised is not working  without internet connection

---

### Post by aysiu on 2006-10-05
Well, unless you have the **Kubuntu Alternate CD**, you're shit out of luck.

You can't install Kubuntu *in addition to* your current Ubuntu using the **Kubuntu Desktop CD**. The only things you can do with a Desktop CD are run a live session or install *in place of* your current installation.

If you have the Kubuntu Alternate CD: ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install kubuntu-desktop
```

---

### Post by umairsaeed219 on 2006-10-05
How can i get Kubuntu alternate cd
i have got my current ubuntu and kubuntu cds from shipit

---

### Post by meng on 2006-10-05
Looks like you will be needing a friend with an internet connection and a CD burner.

---

### Post by aysiu on 2006-10-05
I would download it using BitTorrent over your dial-up connection (start downloading before you go to sleep--it should be finished by the time you wake up).

BitTorrent is preferable to a straight download, as it can be interrupted and continued. It's also more likely to give you an uncorrupted image.

---

### Post by digimars on 2006-10-16
Does this get rid of the gnome files, or how do you do that?

---

### Post by aysiu on 2006-10-16
> **digimars said:**
> Does this get rid of the gnome files, or how do you do that?
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

---

