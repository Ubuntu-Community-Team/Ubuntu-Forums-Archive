---
title: "Splash screen gone after 2.6.12-10-686-smp kernel upgrade?"
date: 2005-12-29
forum: General Help
---

### Post by CheetahCat on 2005-12-29
Hello folks,

I just installed Kubuntu Breezy and applied all updates that were available. Since I have a SMP machine (two processors) i thought it might be a good idea to install the SMP kernel, in order to get most out of my machine.

Since the update has happend, the Kubuntu boot splash screen has gone. I think that the grub config might has been modified.

My entry in menu.lst is the following:
> ...
kernel      /boot/vmlinuz-2.6.12-10-686-smp root=/dev/hda1 ro quiet splash
...

Has somebody an idea how to get the nice splash screen back? :)


Thanks a bunch!
Cheetah

---

### Post by NeoChaosX on 2005-12-29
Tried
```
sudo dpkg-reconfigure linux-image-`uname -r`
```?

---

### Post by CheetahCat on 2005-12-30
Thanks,

that worked like a charm. :)


~ Cheetah

---

