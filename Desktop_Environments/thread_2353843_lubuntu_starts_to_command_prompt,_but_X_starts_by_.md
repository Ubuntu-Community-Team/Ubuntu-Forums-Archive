---
title: "lubuntu starts to command prompt, but X starts by pressing Alt+F7"
date: 2017-02-25
forum: Desktop Environments
---

### Post by strtr101 on 2017-02-25
Hi there,

I am quite new to lubuntu and had some trouble with pcmanfm and thunar and installed/removed perhaps a little too much packages.
Now my system starts to the command prompt and my X11 session only starts up, if I press Alt+F7.
What can I do to make it start up by default again?

I searched the forum but did not find the solution, as dmesg tells me
"[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-4.4.0-64-generic root=/dev/mapper/ubuntu--vg-root ro quiet splash vt.handoff=7"
and this should not lead to a command prompt boot, correct?

Thank you very much for your help!

---

### Post by strtr101 on 2017-03-06
Hi there,

I found the problem, in case it might help somebody else.

I had installed lxdm and lightdm and that made lightdm not start correctly.

Uninstalling lxdm with:
[FONT=courier new]sudo service lxdm stop
sudo apt remove lxdm
sudo service lightdm start
[FONT=arial]
did the trick ...[/FONT]
[/FONT]
CU.

---

