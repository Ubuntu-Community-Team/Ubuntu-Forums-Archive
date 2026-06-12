---
title: "Wireless card prevents hibernation....."
date: 2006-07-31
forum: Desktop Environments
---

### Post by awalsh on 2006-07-31
Hi,

I have a Ibm Thinkpad R51e running Ubuntu Dapper, im using a Belkin Wireless adapter to use my wireless network. This is not the issue, the issue arises when i try to hibernate the laptop (suspend2disk), the hibernation process never begins. So i tried to run hibernate from a terminal using the command:

(below is the terminal output)

```
andrew@andrew-laptop:~$ sudo hibernate
Some modules failed to unload: rt2500
hibernate: Aborting suspend due to errors in ModulesUnloadBlacklist (use --force to override).

```

It appears that RT2500 module is used by the wirless card (i assume), if i use the --force option then hibernation works perfectly and i can resume just by pressing the power button. So my question is how can i force rt2500 to unload so i can use the hibernate option from the quit menu or from the power management features?

Any help would be greatly appreciated

Thanks

Andrew

---

### Post by awalsh on 2006-07-31
Is there any way to add the --force option to the hibernation command called by the quit menu and the on lid close event?

---

### Post by giacomolg on 2006-08-02
> **awalsh said:**
> Is there any way to add the --force option to the hibernation command called by the quit menu and the on lid close event?

I don't know if it will help, but try to make an alias in /etc/bashrc
:-k

---

### Post by JShadow on 2006-08-05
I have the same issue when trying to hibernate using KPowersave. It must be a bug with the module.

---

