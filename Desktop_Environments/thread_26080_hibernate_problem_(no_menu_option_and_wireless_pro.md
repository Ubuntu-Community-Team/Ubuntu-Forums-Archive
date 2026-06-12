---
title: "hibernate problem (no menu option and wireless problems)"
date: 2005-04-11
forum: Desktop Environments
---

### Post by burlap on 2005-04-11
When I installed Hoary there was an option in the log-out menu to hibernate the computer. 

But after I updated from Warty (the same computer, different partition, dual boot "clean" Hoary and Hoary upgraded from Warty), this option is missing (I have ubuntu-desktop, all acpi files in /etc/acpi and /etc/default/acpi-support are the same on upgraded and clean Hoary, resume options are enabled both in mkinitrd and grub).

Also, when I first tried this option (in clean Hoary) it worked great, but it did not after I installed my wireless card. 

In upgraded Hoary I tried running hibernate.sh (wireless card goes off, the system doesn't - it's waiting for wlan to go off...) and later also wireless.sh followed by hibernate.sh. The system freezed (still in Gnome). I waited 5 minutes (CPU was under heavy load judging from the sound of the fan) and turned it off (no other tty was available, I don't know what happened). 

I haven't changed anything in /etc/default/apci-support, so there is suspend to disk. And the same (default) config worked without wireless. 

**UPDATE:**
I tried to do it manually: after bringing wlan down and unloading ndiswrapper, hibernate works (shuts down, reloads with wlan0 on and everything working well).

So my questions:
1. How to enable hibernate option in the menu?

2. How to make scripts properly disable my wireless? (I have placed ndiswrapper in modules to unload in acpi-support, with no effect). Or is it correct?
```
MODULES="ndiswrapper"
```
3. I can make a workaround solution: make own script, a very brutal one:
```
ifdown wlan0
rmmod ndiswrapper
/etc/apci/hibernate_renamed.sh
```
And I can name this script "hibernate.sh", rename the original hibernate.sh, place my fake hibernate in /etc/acpi - if it helps for enabling the option on the menu. 

4. Of course, I can make a launcher for my brutal script anywhere (panel/ desktop), but I want to have it all where it is supposed to be...

Any ideas?

---

