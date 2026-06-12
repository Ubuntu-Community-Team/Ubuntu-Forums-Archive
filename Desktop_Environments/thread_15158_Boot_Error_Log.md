---
title: "Boot Error Log ?"
date: 2005-02-12
forum: Desktop Environments
---

### Post by carlc on 2005-02-12
If a system gets an error while booting, where is the error logged?

---

### Post by mendicant on 2005-02-12
It depends.  Try doing

% dmesg

If you don't see your error, try looking /var/log/messages, /var/log/debug.log and other logs in there.

---

### Post by drasko on 2005-02-12
For getting the whole boot log, enable the bootlogd deamon, editing the file in /etc/defaults/bootllogd, and saying: Yes. After that at the beginning of the boot daemon is started and stoped at the end. Afer logging in check out /var/log/boot for all the informations you've seen during the boottime.

Also, you can search for various informations in /var/log, since there are manny log files. Good place to start is dmsk, as mentioned before.

Bye,
Drasko

---

### Post by carlc on 2005-02-12
Thanks again for the replies. The error that I am getting is the modprobe: Fatal: error inserting shpchp... error. I search the forums and realized that this seems to be a common error.

---

### Post by drasko on 2005-02-13
>The error that I am getting is the modprobe: Fatal: error inserting shpchp... error. I search the forums and realized that this seems to be a common error.

You're right with that - it's a common error, an I experienced this with gentoo too.
It is not such a big problem though, and it is a module that comes with the hotplug service. To solve this go to the /etc/hotplug , an edit the blacklist file, adding this module to blacklist. There is big possibility that you'll have to add and pciehp module here. After that they won't be evoket at the boot...

Drasko

---

### Post by wiseisme on 2005-02-16
Hmmm, If you experienced this error in Gentoo, it means you compiled your kernel with PCI Hotplug support when your mainboard does not support PCI hotplugging.  Apparently Ubuntu has PCI hotplugging enabled   too.

It's a common error, because only the newest of mainboards actually support PCI Hotpluging, that is the ability to swap out PCI cards while the machine is running.

Why anyone would want to remove their cover and start changing cards with the power on and the system booted up in the first place is beond me. Anyways thanks for letting us know how to get rid of the error, this could really scare alot of newbies away when they see boot up errors flying across the screen.

---

