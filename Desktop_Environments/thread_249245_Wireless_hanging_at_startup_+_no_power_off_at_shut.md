---
title: "Wireless hanging at startup + no power off at shutdown fixed"
date: 2006-09-02
forum: Desktop Environments
---

### Post by prahari on 2006-09-02
I installed Ubuntu 6.06LTS 2 weeks ago, and after the first system update, I had the 2 following issues:
1 - when shutting down, the system did not power off.
2 - startup hanging at the "Configuring Network Interfaces" if my wireless card was inserted,

These 2 issues are now fixed,but as I am beginner in Linux, the solutions I found are not really "elegant". I am using an IBM thinkpad A21m, RAM 256 MB, wireless card Netgear WG511.

1 - shutdown with no power-off:
-------------------------------
I added a parameter "acpi=off" to the startup options in the GRUB menu. My default startup entry in /boot/grub/menu.lst is now:

[INDENT]title           Ubuntu, kernel 2.6.15-26-386 (no acpi)
root            (hd0,1)
kernel          /vmlinuz-2.6.15-26-386 root=/dev/hda3 ro quiet splash acpi=off
initrd          /initrd.img-2.6.15-26-386
savedefault
boot
[/INDENT]

2 - startup hanging with wireless card:
---------------------------------------
After multiple attempts, I found out that the nework configuration process was hanging when trying to connect to my wireless router. To fix the issue:

* First, I removed the line "auto wlan0" from the file /etc/network/interfaces:
[INDENT]auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

#auto wlan0
iface wlan0 inet dhcp
wireless-essid XXXXXX
[/INDENT]


* Then, I created a script file that would run at startup to configure and activate the wireless card, and at would de-activate it at shutdown.

- Create the file /etc/init.d/wg511_pra (I copied the structure from /etc/init.d/networking):

[INDENT]$sudo vi /etc/init.d/wg511_pra
... (see attached file) ...
$ sudo chmod 755 /etc/init.d/wg511_pra
[/INDENT]

- Then, I created a link to this file in 2 directories.
[INDENT]
# This creates a link in the directory that lists
# the commands to be run during the shutdown (runlevel 0).
# The "K30" prefix determines at which stages the script will be run.
#
$ cd /etc/rc0.d
$ ln -s ../init.d/wg511_pra K30wg511_pra

# This creates a link in the directory that lists
# the commands to be run during the startup.
# The "S81" prefix determines at which stages the script will be run.
#
$ cd /etc/rcS.d
$ ln -s ../init.d/wg511_pra S81wg511_pra
[/INDENT]


Ok, it is not a very nice solution, but until now, it works fine. I was disappointed when I first had these issues, as I never had them while using Libranet 3.0. But I kept trying to find a solution, as I consider Ubuntu / Kubuntu as a very good distribution.

I hope this can help other people having the same problems.

---

