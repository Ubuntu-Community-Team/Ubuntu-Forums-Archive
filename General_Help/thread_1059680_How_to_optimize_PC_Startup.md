---
title: "How to optimize PC Startup"
date: 2009-02-04
forum: General Help
---

### Post by Johnteresa on 2009-02-04
My system takes a very long time to Startup and shutdown. It's very annoying for me. Plz suggest some software to manage and optimize system startup.

---

### Post by kerry_s on 2009-02-04
don't turn it off or use suspend and hibernate.

your giving us nothing to go on, what are the specs of this slow system? post your /var/log/dmesg.log so we can check it for errors.

---

### Post by gtdaqua on 2009-02-10
> **ortizhector said:**
> *spam deleted*

looks like this is for windows with registry improvement etc. how does this apply for a ubuntu user?

---

### Post by UbuntuNerd on 2009-02-10
try this
open the boot menu configuration file in Gedit by typing this code in a terminal:
```
gksu gedit /boot/grub/menu.lst
```
find the line that reads timeout 10 and change the 10 to read
either 1 or more, for a one second countdown, or 0, to disable the boot menu
completely but if you're doing a dual boot with something else I wouldn't do 0 because you won't be able to see the boot menu, make sure you hit save and reboot to see if is better.
I set mine at 3 and it boots pretty fast hope this helps.

---

### Post by UbuntuNerd on 2009-02-10
for an easier way install "startup manager" from synaptic package manager

---

### Post by neu2buntu on 2009-02-10
goto >system >preferences>sessions and untick some options that u dont really need for e.g bluetooth ,print queue, visual assistance , anything that is not a system dependency ,..this shoud cut a fraction of boot time

---

