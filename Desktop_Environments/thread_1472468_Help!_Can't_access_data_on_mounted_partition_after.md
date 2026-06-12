---
title: "Help! Can't access data on mounted partition after upgrade to 10.04"
date: 2010-05-04
forum: Desktop Environments
---

### Post by zoomiest on 2010-05-04
Yesterday, I upgraded to the 10.04 verion of xubuntu. Looks fine.
However, I keep my data on an NTFS partition of my dual boot laptop, and am finding that I can't access it.

I have a symbolic link to that mounted partition, and when I click on it, I can see the first level of folders, but I can't execute them (even though they seem to be set to 777) and I can't open anything...

Help! I have a lot of work to do today!

Any thoughts?

---

### Post by Jose Catre-Vandis on 2010-05-04
How do you mount it? I usually fresh install and have to create a new mount point and entry in fstab. Something like:
```

sudo mkdir /media/DATA
sudo mount /dev/sda2 /media/DATA

```
Should do it manually and an entry such as:
```

UUID=XXXXXXXXXXXXXXXXX  ntfs-3g  /media/DATA  defaults 0 0

```
in fstab

To get the UUID:
```

sudo blkid

```

(Doing this from memory so hopefully got the syntax right!)

---

### Post by sunk8 on 2010-05-04
You might find the 'mount-manager' app very useful...
Do let us know...

---

### Post by zoomiest on 2010-05-04
"mountmanager" looks like an easy tool to use. I got creative with the settings at first, so, I couldn't mount my drives. Only when I set it back to defaults, would it then work... (would it mount the drives)

I still can't ready my data on the NTFS partition, so I had to boot to windows, to get something done today...

Let me know if there is a resolution to this problem...

---

### Post by Jose Catre-Vandis on 2010-05-04
> **zoomiest said:**
> "mountmanager" looks like an easy tool to use. I got creative with the settings at first, so, I couldn't mount my drives. Only when I set it back to defaults, would it then work... (would it mount the drives)

I still can't ready my data on the NTFS partition, so I had to boot to windows, to get something done today...

Let me know if there is a resolution to this problem...

Did you try the command line options I suggested? If so still no good?

---

### Post by zflyer on 2010-05-05
From your description you may experiencing the following TWO bugs that Xubuntu 10.04 has:

thunar select freezes after using mouse to select folders ("detailed view" mode) 
[https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/520118](https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/520118)

Xubuntu 10.04 USB, CD and DVD automount fails if autologin is on
[https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/546992](https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/546992)

no fix released yet.

---

### Post by zoomiest on 2010-05-12
Jose,
I _did_ try the settings you suggested, but I think that the bug mentioned above, (only the top thunar one) is what we are dealing with...

I will see if I can load another file manager...

Thanks all...

---

