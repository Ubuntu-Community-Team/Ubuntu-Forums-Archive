---
title: "Edited Fstab. Now it's a &quot;Read only file sytem?&quot;"
date: 2005-09-30
forum: Desktop Environments
---

### Post by poopdog on 2005-09-30
Hello.

I tried to edit my etc/fstab to include my windows NTFS and my fat32 partitions.

First I entered my NTFS info and rebooted and it worked just fine.

Then when I typed in the fat32 partition information and restarted, I think I entered something wrong.

When I rebooted, it did some checking of the fat32 disk, then dropped into terminal.

So, I went into etc/ folder and tried to do a ed fstab (even tried with an su as well)

But now I get the following error when trying to just ed it:

open_sbut: Tmpfile() failed with 'read-only file sytem'

What does this mean exactly, and how do I fix it?

---

### Post by poopdog on 2005-09-30
I restarted in recovery mode and worked around a little bit.

I got it working.

---

