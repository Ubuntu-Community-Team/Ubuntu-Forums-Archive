---
title: "installed compiz on new partition (shared /home) broke the other partition!"
date: 2013-04-30
forum: Desktop Environments
---

### Post by brallan on 2013-04-30
I want to have two partitions with installs sharing the same /home folder. In addition to an existing partition with ubuntu 12.04, I created a new partition, installed lubuntu 13.04. After installing compiz and tweaking it a bit, the changes to the /home partition must have affected the other partition, because 12.04 boots up but can't make the windows work. I guess ubuntu depends on compiz to work?

what can I do to fix this sort of incompatibility? help anyone?

---

### Post by ajgreeny on 2013-04-30
Is your /home partition separate to your two OS partitions?  If so it should not specifically be compiz that is causing the problem, but perhaps differences in versions of some of the applications on both OSs that keep their configuration files or folders in /home.

This may be one of the situations where it is better to keep /home in the root partition of each OS and share only a data partition.

---

### Post by brallan on 2013-05-01
> **ajgreeny said:**
> Is your /home partition separate to your two OS partitions?  If so it should not specifically be compiz that is causing the problem, but perhaps differences in versions of some of the applications on both OSs that keep their configuration files or folders in /home.

Yes, the home partition is on /dev/sda6 and the other two are /dev/sda1 and /dev/sda5. But I can't understand what else it could be other than compiz.... which application could that be? the desktop environment is openbox-lxde for lubuntu13.04, and unity for ubuntu 12.04, No?

---

### Post by mcduck on 2013-05-01
Unity desktop runs on top of Compiz, so if you share the home directory and tweak your Compiz settings the same settings will apply to Unity side as well (and quite likely break Unity).

I wouldn't usually recommend sharing the whole home directory between separate OS installs, but rather just create some shared data directories instead to access your files form each OS while still allowing each OS to maintain their own settings.

---

### Post by ajgreeny on 2013-05-01
Yes, I see what you mean.  I think the problem is probably related to  the fact that your compiz settings are contained in a configuration  folder or file in your shared /home; I'm not sure exactly where as I  don't bother with compiz on my Xubuntu.  Unity is very fussy about the  compiz settings that are acceptable to it, and I suspect your tweaks of  unity in Lubuntu will now have made unity non-functioning.

To try to get things back in unity use commands
```
gconftool-2 --recursive-unset /apps/compiz
unity --reset
```

**mcduck**  got there whilst I was called away from my computer, but says basically  the same thing.  Get compiz running again in unity in Ubuntu, and then  do not tweak it again in Lubuntu and you should be OK

---

