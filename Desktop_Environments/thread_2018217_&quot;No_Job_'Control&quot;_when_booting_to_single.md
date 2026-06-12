---
title: "&quot;No Job 'Control&quot; when booting to single user mode and invoking &quot;init=/bin/sh&quot;"
date: 2012-07-06
forum: Desktop Environments
---

### Post by dsluser on 2012-07-06
Hi All, 

I'm trying to package a vm of Ubuntu which will force a user to change hostname on first boot. 

I'm using Ubuntu 11.10, release version with minimal updates.

I have a script that does this successfully for Fedora. I have adjusted the script for Ubuntu, however Ubuntu does not seem to support auto-login to runlevel 1 without a root password (It is not an option to not set root password on these machines)

The reason I want this is in order to run an interactive script at first boot. My script then sets the hostname, removes itself from /etc/bash.bashrc and sets runlevel to 5(or 2 in Ubuntu)

I thought I had found a work around by editing /etc/default/grub to have "single init=/bin/bash"

However when I reboot after setting this I'm seeing the shell but with 
bash: cannot set terminal process group (-1): Inappropriate ioctl for device
bash: no job control for this shell

From this shell I cannot write any files, reboot or pretty much do anything. Can anyone help me out here?

Grub below 

setparams 'Ubuntu, with Linux 3.0.0-12-generic

recordfail
set gfxpayload=$linux_gfx_mode
insmod gzio
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root <uuidhere>
linux /boot/vmlinuz-3.0.0-12-generic root=UUID=<uuidhere> ro quiet splash vt.handoff=7 single init=/bin/bash
initrd /boot/initrd.img-3.0.0-12-generic

---

### Post by dsluser on 2012-07-06
I've made some progress - the system was being mounted read only, using rw in the grub options didn't help.

The only issue I have now is that I cannot reboot the machine, I keep getting 
"shutdown: Unable to shutdown system" 

and telinit 6 returns 

"telinit: Failed to connect to socket /com/ubuntu/upstart: Connection refused"

As per the post at [http://linuxforums.org.uk/index.php?topic=6551.0]("http://linuxforums.org.uk/index.php?topic=6551.0") you run "mount - o remount,rw /" when you log in to this shell.

---

### Post by dsluser on 2012-07-06
Any upstart gurus able to help out? I assume this issue is because I'm invoking init?

---

