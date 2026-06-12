---
title: "reiserfs crashed, can't run fsck to fix"
date: 2009-02-13
forum: General Help
---

### Post by man_bash on 2009-02-13
Hello,
My main partition with linux had crashed, and I can't boot into Ubuntu, it crashes on startup,saying I need to run fsck. When I load into "recovery" and login as root, run fsck - it tells me that the journal has some problems, and I need to run fsck with "--rebuild-tree" parameter to fix it, but when I try to run "fsck --rebuild-tree" nothing happens - just the same message that shows when you type in "fsck -h". The computer doens't load any other filesystems, so just running fsck with some working keys (ie -r) works fine, but doesn't fix the problem. I simply want to salvage the files, I'd reinstall in a flash if I didn't have the files stuck on that partition... Any ideas?

---

### Post by man_bash on 2009-02-14
Bump

---

### Post by dcstar on 2009-02-14
> **man_bash said:**
> Hello,
My main partition with linux had crashed, and I can't boot into Ubuntu, it crashes on startup,saying I need to run fsck. When I load into "recovery" and login as root, run fsck - it tells me that the journal has some problems, and I need to run fsck with "--rebuild-tree" parameter to fix it, but when I try to run "fsck --rebuild-tree" nothing happens - just the same message that shows when you type in "fsck -h". The computer doens't load any other filesystems, so just running fsck with some working keys (ie -r) works fine, but doesn't fix the problem. I simply want to salvage the files, I'd reinstall in a flash if I didn't have the files stuck on that partition... Any ideas?

If it is you "main" partition then you cannot repair a filesystem you have mounted, boot off a Live CD and then run fsck.

---

### Post by man_bash on 2009-02-15
Thanks, that makes sense :cool:

I actually have 2 partitions with linux (one 8.04 i386, and one 8.10 AMD64). Both are screwed the same way (is it linux issue, reiserfs issue, or a Western Digital issue? I think it's WD's fault...). So you say I should launch the i386-Hardy to check the AMD64 distro and vice-versa?

Also, would I use ```
sudo mount /dev/hda1/ /mnt/hda1/
``` to properly mount a filesystem, or do I need some other keys to mount it the way fsck wants them?

Also, how can I check which partition is which? I have 5 partitions on that 320 Gb HDD, plus 4 Gb swap...

Thank you

---

