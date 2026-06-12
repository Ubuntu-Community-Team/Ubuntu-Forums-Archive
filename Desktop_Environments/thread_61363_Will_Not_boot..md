---
title: "Will Not boot."
date: 2005-08-31
forum: Desktop Environments
---

### Post by Maxplayer14 on 2005-08-31
EXT3-fs error (devic had1): ext2_find_entry:  reading directory #179873 offset 0.

That is the error I get when I am trying to boot.

I was ssh'ed into this machine and did a reboot.  And couldn't ssh back in.

So I came the the physical location of the machine and tried to reboot this is what happens.

Is my hardrive failed?

I tried to boot into the safe mode but that didn't work either.

Any suggestions?

---

### Post by shakin on 2005-08-31
Boot from a live cd and run 'e2fsck -c /dev/hda1'

That will check the disk for errors and correct any that it can. It's weird that you got this error at all. I can see maybe if the system lost power suddenly, but a proper reboot shouldn't cause hard drive corruption.

---

