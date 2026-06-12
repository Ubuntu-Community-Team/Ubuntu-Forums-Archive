---
title: "thinkpad-base and tpctl issues"
date: 2006-07-08
forum: Desktop Environments
---

### Post by drx on 2006-07-08
I am having issues with my Thinkpad X41 ... under Kubuntu Dapper, the hotkeys for "Thinklight", "Access IBM" key, "zoom" and "brightness" are working fine through a KDE Controlcenter Module and KLaptop. 

However, all other hotkeys (concerning hibernation) do nothing and KLaptop is not able to set the system into sleep or hibernation mode. In "sleep", the moon symbol on the computer is glowing, but the cpu fan continues to run and the computer cannot wake up anymore. Hibernate has the same effect, but before there is some harddisk spinning going on.

I have installed the thinkpad-base and tpctl packages. But tpctl complains that it cannot find /dev/thinkpad ... indeed, there is only /dev/nvram ... and since i made myself a member of the group "nvram" the KDE supported options started to work.

As far as i understand, thinkpad-base is supposed to enable the /dev/thinkpad hierarchy? But where is it gone? How to enable it?

Did anybody get this to work?

For a laptop computer this is quite annoying ... any help welcome.

---

