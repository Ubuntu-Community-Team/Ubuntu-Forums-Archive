---
title: "/etc/sudoers syntax error, how can I fix?"
date: 2005-12-12
forum: Desktop Environments
---

### Post by pr0fess0r on 2005-12-12
Hi
I mistakenly edited /etc/sudoers and used a colon where I should have used a comma, now I can't repair the file or do anything sudo as sudoers isnt valid, si there a way to fix this...?

cheers

---

### Post by computerbs on 2005-12-12
[QUOTE=pr0fess0r]Hi
I mistakenly edited /etc/sudoers and used a colon where I should have used a comma, now I can't repair the file or do anything sudo as sudoers isnt valid, si there a way to fix this...?

cheers[/QUOTE]

I'm assuming you don't have root privileges, eh? ;-)

First of all, NEVER EDIT /etc/sudoers directly.  Use visudo.  If you get syntax errors, visudo will warn you so you don't get into this trouble.

OK, how to fix this?

If you have a Ubuntu system disk, or even the Ubuntu installation disk, it's a snap.

First of all, make note of your root partition (the partition whith /etc/).  I was able to figure it out from typing 'mount' all by itself.  The first line of output said this:

/dev/sda1 on / type ext3 (rw,errors=remount-ro)

which means that /dev/sda1 is my root partition.  Jot this down for later.

If you have the installation CD, simply reboot and boot from the CD.  You will probably need to answer the first few questions (as you did when you first installed ubuntu) such as the name for the computer, etc.  As soon as you see an option to go 'Back', select it.  You should hopefully see a list of all the installation steps.  Down a bit, you should see the item, "Execute a shell".  Do this.

From the shell, you need mount the root partitition somewhere.  Here's an example:

cd /
mkdir /mnt
mount /dev/sda1 /mnt  (use the YOUR root partition, the one you jotted down)
cd /mnt
cd etc
nano sudoers

nano is the text editor available from within the setup.  FIX your sudoers file, then reboot normally.  All should be well again...

---

### Post by doclivingston on 2005-12-12
Alternatively: when grub comes up, select the "Recovery Mode" option, which drops you into a root shell.

---

### Post by pr0fess0r on 2005-12-12
Actually I found this post:
[http://ubuntuforums.org/archive/index.php/t-14366.html](http://ubuntuforums.org/archive/index.php/t-14366.html)

And followed those instructions:
In grub, on bootup, switch to the menu and update the kernel command:
kernel /boot/vmlinuz-2.6.8.1-4-386 root=/dev/hdb2 ro quiet splash rw init=/bin/bash
that booted me into the prompt and I fixed it. That'll learn me!
thanks for the prompt help guys

---

### Post by computerbs on 2005-12-12
[QUOTE=doclivingston]Alternatively: when grub comes up, select the "Recovery Mode" option, which drops you into a root shell.[/QUOTE]


Even better! ;-)

I am so "old school".  Gotta learn how to do things the easy way!

---

