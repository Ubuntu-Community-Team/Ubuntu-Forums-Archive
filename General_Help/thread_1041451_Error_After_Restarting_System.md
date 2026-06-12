---
title: "Error After Restarting System"
date: 2009-01-16
forum: General Help
---

### Post by Five Star on 2009-01-16
I'm a noob and recently have been messing around with Ubuntu 8.10. I've have been trying to get compiz-fusion to work, but have not yet.

Whenever I try to activate my driver, like version 177 or something, I keep getting this error message when I restart my computer:

"Ubuntu is running in low-graphics. The following error was encountered, you may need to update your configuration to solve this. 

(EE) NVIDIA (0): Failed to load the NVIDIA Kernal module!
(EE) NVIDIA (0): ***Aborted***
(EE) Screen(s) found, but none have a usuable configuration."

Then I just go back to my original settings and haven't solved this problem...

Please help! Thanks in advance!

---

### Post by Five Star on 2009-01-16
If this helps at all, I installed Ubuntu through wubi on my external hard drive. I can also reboot into vista.

---

### Post by Five Star on 2009-01-17
Bump, please...I really want to use ubuntu/compiz.

---

### Post by RJARRRPCGP on 2009-01-17
> **Five Star said:**
> I'm a noob and recently have been messing around with Ubuntu 8.10. I've have been trying to get compiz-fusion to work, but have not yet.

Whenever I try to activate my driver, like version 177 or something, I keep getting this error message when I restart my computer:

"Ubuntu is running in low-graphics. The following error was encountered, you may need to update your configuration to solve this. 

(EE) NVIDIA (0): Failed to load the NVIDIA Kernal module!
(EE) NVIDIA (0): ***Aborted***
(EE) Screen(s) found, but none have a usuable configuration."

Then I just go back to my original settings and haven't solved this problem...

Please help! Thanks in advance!

Looks like it's because you're missing the kernel headers! I just had the same symptoms with a custom Ubuntu install.

Did you install with the Ubuntu minimal CD? 

There appears to be an issue where the kernel headers are not installed by default when you install Ubuntu with the minimal CD.

Please use the following:

```
sudo apt-get install linux-headers-generic dkms nvidia-glx-177 && sudo nvidia-xconfig
```

That worked like a charm for me.

---

### Post by Five Star on 2009-01-18
> **RJARRRPCGP said:**
> Looks like it's because you're missing the kernel headers! I just had the same symptoms with a custom Ubuntu install.

Did you install with the Ubuntu minimal CD? 

There appears to be an issue where the kernel headers are not installed by default when you install Ubuntu with the minimal CD.

Please use the following:

```
sudo apt-get install linux-headers-generic dkms nvidia-glx-177 && sudo nvidia-xconfig
```

That worked like a charm for me.

Yes!!!!

YEAH!!!

It worked!

Thank you for your help, I appreciate it very much.

---

