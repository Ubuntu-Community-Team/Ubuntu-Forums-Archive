---
title: "Permission change on dynamically created device node?"
date: 2006-08-25
forum: Desktop Environments
---

### Post by kikinovak on 2006-08-25
Hi,

I just painfully setup a HP PSC 750 printer/scanner combination. Everything works *almost* fine, except I need rw-rw-rw- permissions on /dev/usblp0. Of course, I can always chmod 666 /dev/usblp0 before setting the thing up, but then it will be gone on the next rebooting, or when I switch off or otherwise unplug the printer. Then it will be rw-rw-r-- again, and HPLIP will complain and refuse to work.

Before using Ubuntu, I've been using Slackware for some time, and I knew how to solve this kind of problem: edit /etc/udev/rules.d/udev.rules, and change the permissions there. Restart udev, and everything would be fine.

But things seem to work a bit differently in Ubuntu. I took a peek in /etc/udev/rules.d/ , but there are plenty of files there. 

Anyone knows which file has to be edited - and how? - in order for /dev/usblp0 to come up with 666 permissions?

Cheers.

---

### Post by conner on 2006-08-31
Hi, my solution under Breezy:
$> sudo vi /etc/udev/rules.d/020-permissions.rules
~
     # USB devices
     BUS=="usb", KERNEL=="legousbtower*", MODE="0666"
     BUS=="usb", KERNEL=="lp[0-9]*", GROUP="lp" [COLOR="Red"]MODE="0666"[/COLOR]
     BUS=="usb", KERNEL=="ub[a-z]*", NAME="%k", MODE="0640", GROUP="plugdev"
~
do the red changes at the line above, if that dos not works for you try to find a more applicable entry. It works for 'kqemu' the accelerator of qemu by adding the line

# kqemu acceleration
     KERNEL=="kqemu"         MODE="0666"

I hope this would help anyone stucks in '/dev' permission problems :twisted:  under ubuntu

cu
conner :)

---

