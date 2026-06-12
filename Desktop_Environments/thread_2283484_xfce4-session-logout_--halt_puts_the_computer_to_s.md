---
title: "xfce4-session-logout --halt puts the computer to sleep"
date: 2015-06-22
forum: Desktop Environments
---

### Post by k0ral on 2015-06-22
Hello,

I'm having troubles shutting down my computer through the xfce panel (which executes xfce4-session-logout). When I select "Shutdown" through the graphical menu, my computer goes to sleep instead of shutting down.
I also tried executing "xfce4-session-logout --halt" in a terminal, and got the same result. However, when I execute "systemctl halt" in a terminal, the computer correctly shuts down.

This suggests there is an issue in the xfce4-session-logout binary. Could you please assist ?

Thank you !

*Note: I'm not the only one using this computer, and other users are not too fond of the commandline so I really need to get this graphical menu to work for them.*

---

### Post by kerry_s on 2015-06-22
what xubuntu version ? 14.04 ?
make & model of pc ?

for now you can just create a panel launcher to run the "systemctl halt" command.

---

### Post by k0ral on 2015-06-23
I'm using xubuntu version 15.04, as advertised by the lsb_release -a command.
I have no clue about the maker of the PC, I didn't buy it myself, even the dmidecode command gives no information.
 The model is M116 SU7300, as indicated by a sticker under the laptop.

Also, an erratum from my initial description: "systemctl halt" doesn't manage to halt the computer, it gets frozen during the shutdown splash screen of xubuntu with the animated circle. But at least it tries to actually halt the computer, contrary to the graphical panel which simply puts it to sleep.

---

### Post by kerry_s on 2015-06-23
use the file manager to go to /var/log
look at kern.log & syslog

maybe there&#8217;s a clue in there. you might also try checking the bios, see what the settings are set to. if there's a setting for acpi, linux uses S3, so make sure that's selected. might even want to use the reset to default for bios, just in case it's been changed to  something non-standard.

---

