---
title: "Problem with &quot;Resume&quot; drive setting -- trouble finding swap drive"
date: 2008-04-25
forum: Desktop Environments
---

### Post by dawynn on 2008-04-25
I could not successfully burn a copy of the new install disk, so I went the upgrade route.  Used an old Feisty CD I had and upgraded through Gutsy to Hardy.  Working through my issues now.

First issue: I can boot very cleanly from the recovery mode of the latest kernel.  But I have to take off the "splash quiet" settings in order to boot with the regular grub option.  After going through part of the boot, it tries to resume from the swap drive.  It tells me it cannot resume from /dev/hda10.  So I tell it that it needs to use /dev/sda10 and everything else proceeds fine.

So, where might it be getting this information about my swap drive?

/etc/fstab (note that the /dev/hda10 here is a comment):
# /dev/hda10
UUID=4a68dbc9-aa3f-484c-b0a2-f4eb8a02b367 none            swap    sw              0       0

/etc/initramfs-tools/conf.d/resume:
RESUME=UUID=4a68dbc9-aa3f-484c-b0a2-f4eb8a02b367

Where else would it be looking for info about my swap drive?

(added on 4/26/08 )
Thought this might help narrow down the cause.  I hand-copied the text that I'm seeing when I have to reenter the drive label.  So, I'm sorry if this is not 100% accurate -- I couldn't find this text in the logs, so I couldn't just copy and paste.

---------------------------------------------------------------------------------------

Begin: Running /scripts/local-premount ...
kinit: name_to_dev_t (/dev/disk/by-uuid/4a68dbc9-aa3f-484c-b0a2-f4eb8a02b367) = sda10(8,10)
kinit: trying to resume from /dev/disk/by-uuid/4a68dbc9-aa3f-484c-b0a2-f4eb8a02b367
[   28.453400] Attempting manual resume
kinit: No resume image, doing normal boot ...
resume: libgcrypt version: 1.2.4
resume: Could not stat the resume device file '/dev/hda10'
        Please type in the full path name to try again
        or press ENTER to boot the system:

---------------------------------------------------------------------------------------

Any ideas now?

---

### Post by dawynn on 2008-04-28
[ bump ]

---

### Post by dawynn on 2008-04-29
Quick update:

I never did find out what was going on here.  I did, however, go through my system, comparing my current packages to what I had in Gutsy.  I threw out a bunch of stuff.  I also got rid of Xfce and the highly unstable KDE4 in favor of KDE3.  

Somewhere, in the midst of system updates, *something* cleared itself and I no longer have this resume issue.  

So, now I have a PC that can cleanly boot into Windows, Gutsy, and Hardy.  Both Gutsy and Hardy are set up with KDE for its GUI-ness, and IceWM for its leanness.  I'm free of the glaring issues, and everythings looking pretty.

Cheers!

---

