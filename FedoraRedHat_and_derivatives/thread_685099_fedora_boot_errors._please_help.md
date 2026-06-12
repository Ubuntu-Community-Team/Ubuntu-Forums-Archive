---
title: "fedora boot errors. please help"
date: 2008-02-01
forum: Fedora/RedHat and derivatives
---

### Post by swankyfb on 2008-02-01
whenever i turn on my computer, fedora will not boot. there is an error. is there a way of fixing this? it looks somthing like this: booting 'fedora (2.6.23.1-42.fc8)'
root(hd0,0)
filesystem type is ext2fs, partition type 0x83 
kernel /vmlinux-2.6.23.1-42.fc8 img
[Linux-intrd@0x37c66000,0x38969e bytes]
uncompressing linux...OK,booting the kernel.
powernow-k8:invalid powernow-table

---

### Post by RebounD11 on 2008-02-01
That is what it told me last time I installed before booting, but booted fine after all... 

A question however... Why do you use ext2? I find ext3 better :D

---

### Post by swankyfb on 2008-02-01
i don't even know the difference between ext2-3. i don't even know what they are or what they do. so your telling me if i let it load all of those errors it will boot up still? i mean theres a lot of errors lol

---

### Post by igknighted on 2008-02-02
There's more?  The only "error" that you posted is the last line, and even that shouldn't stop it from booting.  Try hitting 'e' when you have the line in the grub bootloader highlighted, then hit 'e' again on the kernel line.  Then erase (at the end of the line) the words "rhgb" and "quiet", or anything that sounds like quiet.  Then hit enter, and then 'b' to boot.  This will boot without trying to load the splash screen and not suppress any messages from being printed to the screen.

Also (@RebounD11), fedora uses LVM (sounds like he did a default install and didn't change out of this).  Ext2 is used because it is merely the /boot partition that is being mentioned.  The actual system in a logical volume, which is almost certainly ext3.  It is typical of distro's that separate /boot from / to use ext2 instead of ext3.  I suspect it is for simplicity and the fact that a journal would likely not be of any importance on such a small partition, but I really don't know why.  I have just noticed that it is convention.

---

### Post by RebounD11 on 2008-02-02
Didn't know that... I always make my own partitions :D I like to have control.

Does anyone know what happened to ext4? I had some partitions formated that way and they seemed ok (checking them every 26 mounts was faster). You couldn't boot from ext4 back then but since I haven't heard a word about them.

I'll google it later :D now that it came up.

---

### Post by swankyfb on 2008-02-02
Thank you very much =)

---

