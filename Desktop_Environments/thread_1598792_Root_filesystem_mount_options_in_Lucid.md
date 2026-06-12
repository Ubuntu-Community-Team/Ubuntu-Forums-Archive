---
title: "Root filesystem mount options in Lucid"
date: 2010-10-17
forum: Desktop Environments
---

### Post by treacl on 2010-10-17
Hi all,

Two questions about mounting the root filesystem with non-default options (ext4 noatime, nodelalloc) in Lucid:

1. In earlier releases, to change mount options for the root filesystem, you had to add the options to /boot/grub/menu.lst as well as /etc/fstab. (For non-root filesystems, you could just change them in /etc/fstab.) Is this still true on Lucid? If so, what's the correct syntax? I haven't been able to find documentation anywhere.

2. How do I verify what options a partition is actually mounted with--not just "is supposed to be mounted with," which is what cat'ing /etc/fstab will tell me? Will "sudo tune2fs -l /dev/..." do the job?

Thanks,
treacl

---

### Post by Darkness Des on 2010-10-17
The 2nd command I am not quite sure about. However, I do have a solution to your first problem. *menu.lst* no longer exists in GRUB2, it has been replaced by a non-editable grub.cfg (not even writable by root) which I don't remember where it has been placed. However, you can edit /etc/default/grub, add your options, and then run the command "sudo update-grub" to add them.

---

### Post by treacl on 2010-10-17
Many thanks, Darkness, for the very quick reply.

I've tinkered with /etc/default/grub before, for other reasons. But I can't figure out what exactly I need to add there to change filesystem mount options (or whether, in fact, I *do* need to add them there). And I haven't been able to find anything in the grub2 documentation.

I assume that the mount options would go in GRUB_CMDLINE_LINUX or GRUB_CMDLINE_LINUX_DEFAULT, but which one? And what exactly goes there? In the old menu.lst, it was something like "rootflags=data=writeback" (for that particular option). Is it still the same? And how does one add multiple options? Are they separated with commas, spaces, etc.?

---

### Post by Darkness Des on 2010-10-17
They are the same commands, to the extent of my knowledge. They go under GRUB_CMDLINE_LINUX

---

### Post by treacl on 2010-10-17
Thanks again, Darkness.

I've done a little digging around and experimenting and think I've figured out the following:

1. You only need to enter the mount options in /etc/fstab, and whatever you have in /etc/fstab seems to override whatever you put in /etc/default/grub (or enter on the grub command line).

2. Re determining what options your filesystems are actually mounted with:

[LIST=1]
[*]/etc/fstab = What they should normally be mounted with, not necessarily what they are actually mounted with.
[*]cat /proc/mounts = One version of what they are actually mounted with.
[*]sudo mount = cat /etc/mtab = Another version of what they are actually mounted with.
[*]sudo tune2fs -l /path/to/device = ?
[/LIST]
#2 and #3 above should be the same or very similar. See man mount for an explanation of how and when they may differ.

Since it is apparently possible to put mount options in /etc/default/grub instead of or in addition to putting them in /etc/fstab, it makes me wonder whether there is any advantage to doing so. Anyone who's familiar with this care to weigh in?

Many thanks,
treacl

---

### Post by Darkness Des on 2010-10-17
AFAIK, putting them in /etc/fstab is best.

---

