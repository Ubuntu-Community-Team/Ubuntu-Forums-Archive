---
title: "[solved] printing /dev/usb/lp0 permission"
date: 2006-01-12
forum: General Help
---

### Post by metoo on 2006-01-12
On my amd64 system I had a problem, that my usb printer (brother hl-1430 bw laser) would not print before I either:
set the owner for /dev/usb/lp0 from 'root' to 'lp' and re-started the printer via the web interface
or did:
sudo chmod 666 /dev/usb/lp0 and re-started the printer via the web interface
(this command I found here in the forum)

However, it is annoying to do this on every re-boot.

Solution:
In /etc/udev/permissions.rules under section '# usb devices' change the line:
BUS=="usb", KERNEL=="lp[0-9]*", GROUP="lp"
to:
BUS=="usb", KERNEL=="lp[0-9]*", MODE="0666", GROUP="lp"

Adding 'MODE="0666", '.
Now when powering up the printer after booting the PC you can print immediately.
(Sorry if this was posted before, I did not found this when searching for a permanent solution.)

Update: Sorry, wrong forum, seems that I cannot move this to hardware myself!?

---

### Post by debernardis on 2006-01-12
Thanks a lot! (see [here]("http://www.ubuntuforums.org/showpost.php?p=651132&postcount=3"))

---

### Post by petteri on 2006-01-14
[QUOTE=metoo]On my amd64 system I had a problem, that my usb printer (brother hl-1430 bw laser) would not print before I either:
set the owner for /dev/usb/lp0 from 'root' to 'lp' and re-started the printer via the web interface
or did:
sudo chmod 666 /dev/usb/lp0 and re-started the printer via the web interface
(this command I found here in the forum)

However, it is annoying to do this on every re-boot.

Solution:
In /etc/udev/permissions.rules under section '# usb devices' change the line:
BUS=="usb", KERNEL=="lp[0-9]*", GROUP="lp"
to:
BUS=="usb", KERNEL=="lp[0-9]*", MODE="0666", GROUP="lp"

Adding 'MODE="0666", '.
Now when powering up the printer after booting the PC you can print immediately.
(Sorry if this was posted before, I did not found this when searching for a permanent solution.)

Update: Sorry, wrong forum, seems that I cannot move this to hardware myself!?[/QUOTE]

I am having the same problem, but I cannot find the exact line as listed above and I'm afraid to change anything without checking here first!

Here is what I have:

> # USB devices
BUS="usb", KERNEL="hiddev*",	NAME="usb/%k"
BUS="usb", KERNEL="auer*",	NAME="usb/%k"
BUS="usb", KERNEL="legousbtower*", NAME="usb/%k"
BUS="usb", KERNEL="dabusb*",	NAME="usb/%k"
BUS="usb", KERNEL="lp[0-9]*",	NAME="usb/%k"
BUS="usb", KERNEL="cpad[0-9]*",	NAME="usb/%k"


from: /etc/udev/udev.rules

What do I need to change here? Or is this the wrong file? 

Thanks!

EDIT: I'm running HOARY if that matters...

---

### Post by metoo on 2006-01-15
You probably found that yourself already:

It is the wrong file. Look into
/etc/udev/permissions.rules

( and not  /etc/udev/udev.rules)

However, udev changed a lot recently and breezy is already much younger than hoary, so using hoary can make a difference.
Check in the right file first. If you find the line, it should be OK.
Make a copy of the original file before changing, so if things go wrong you can just copy it back.

---

### Post by petteri on 2006-01-15
Hmm, I can't find that file... here is a copy of the /etc/udev directory:

cd-aliases.rules   compat.rules  permissions.d  simple-cd-aliases.rules
cdsymlinks.conf    devfs.rules   rules.d        udev.conf
compat-full.rules  links.conf    scripts        udev.rules

any ideas?  Thanks!

---

### Post by eoinmadden on 2006-10-31
I found another solution. :) 

Open System > Administration > Users And Groups
Click on Manage Groups
Click on lpadmin
Click on Properties
Tick the users you want to be able use the parallel port.
Click Ok, Close, etc.

---

