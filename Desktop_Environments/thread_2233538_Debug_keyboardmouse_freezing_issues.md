---
title: "Debug keyboard/mouse freezing issues"
date: 2014-07-09
forum: Desktop Environments
---

### Post by bertram2 on 2014-07-09
Good day everyone!

After updating to Ubuntu 14.04 (with additional packages for KDE installed) I experience random freezing of keyboard or mouse on the login screen. Sometimes (not really reproduceable or predictable) either the mouse or the keyboard (both PS/2) is frozen. A reboot normally solves the problem, however, changing to console (if the mouse is frozen) and trying to restart various services (i.e. xserver) doesn't help. Attaching a USB-keyboard (if the keyboard is frozen) works fine, but the PS/2 one stays frozen. Logfiles don't show anything unexpected.

Can you give me any hints of where to look into for deeper diagnosis on what might be causing that problem (i.e. where to look further) and/or what other services I could try to restart in order to narrow down the problem?

Thank's for your replies,

Bert

---

### Post by Bashing-om on 2014-07-12
bertram2; Hello;

I also run an old ps/2 mechanical keyboard on release 14.04 - I have no problems.
I have set in bios "legacy" for my keyboard and as well have enabled all instances of "plug and play".

You might play around with your bios setting and see what results.

[INDENT][INDENT]these processes all start in bios
[/INDENT][/INDENT]

---

### Post by bertram2 on 2014-07-31
Hi bashing-om,

thank's for the reply. I don't think it's some problem that can be solved via bios settings, since it occurs randomly (thus most of the time it works as supposed) - and in the grub menu the keyboard still works.

Maybe the problem's somehow connected to the i8042-driver, I'm not sure though. I'll attach a couple of logfiles and other information that might be helpful:

results of "cat /proc/bus/input/devices": [ATTACH]255169[/ATTACH]
results of "xinput -list": [ATTACH]255170[/ATTACH]
results of "dmesg | grep i8042": [ATTACH]255171[/ATTACH]

One workaround I've just found recently: Suspending and resuming resolves the problem.

---

