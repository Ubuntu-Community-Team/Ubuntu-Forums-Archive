---
title: "Need help on Ubuntu 8.10"
date: 2009-04-09
forum: General Help
---

### Post by silicon_fusion on 2009-04-09
Currently I am using microsoft xp sp3 & Ubuntu 8.10 installed on same hdd.Now i want to reinstall xp( fresh installation )
But if i install xp my ubuntu will lost & i didnot want to lose it.Is there any way to install xp with losing previous version of ubuntu on my hdd.

---

### Post by taurus on 2009-04-09
Did you install Ubuntu with wubi or did you install Ubuntu on it own partition, on the same harddrive?  That makes a big difference.

---

### Post by N_Nick on 2009-04-09
I think what he meant is he has 2 different partitions and is worried about the MBR when he installs XP again.  I saw a tutorial somewhere, let me look and i ll get back to you.

---

### Post by taurus on 2009-04-09
> **N_Nick said:**
> I think what he meant is he has 2 different partitions and is worried about the MBR when he installs XP again.  I saw a tutorial somewhere, let me look and i ll get back to you.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by N_Nick on 2009-04-09
> **taurus said:**
> [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

That's it, cheers :)

---

### Post by Gaweph on 2009-04-09
Yup, that tutorial looks good.

Basicalyl windows will defenatelly overwrite your MBR, so when you restart its going to boot straight into windows, doing that tut will put grub back onto the mbr.

On a side note, what are you using windows for?  I have recently stopped using my windows partition, and started running virtualbox.

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads) <-- you can install windows and run it from yourubuntu install, it allows you to do everything you normally can in windows (except games -- which you can use wine for anyways)

Gaw

---

