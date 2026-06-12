---
title: "I think I screwed up GRUB (among other things)"
date: 2009-06-08
forum: General Help
---

### Post by stuart.reinke on 2009-06-08
I've really done it this time!

I attempted to create an xubuntu/pclinuxos dual boot.

I resized the main partition on hda1 and created hda2 --no problems

Then I tried to install PCLinuxOS on hda2 -- install failed -- error message said "can't copy files to new root"

Then I decided to attempt again at a later date and return my computer back to normal.

ran g-parted live cd again removed hda2 and resized hda1 -- no problems

Rebooted machine -- GRUB loads, Xubuntu shows on screen with progress bar

Some message flashes underneath the progress bar (too fast for me to read)

Computer then boots to a shell login -- does not recognize my login or password -- I can however log in as root

I them am left with a prompt something like this:
    PcLinuxOS ~$]

Through the shell I cannot find any of my files. Probably because I am not looking in the right place.

I can however find everything when using a live cd.

There are two vmlinuz files and two initrd.img files in the root directory one of each has .old on the end (might be important)

Any help is appreciated, I bit off more than I could chew. 

Also,is there any way to gain root access to the file system via Live CD GUI?

---

### Post by VMC on 2009-06-08
> **stuart.reinke said:**
> I've really done it this time!

I attempted to create an xubuntu/pclinuxos dual boot.

I resized the main partition on hda1 and created hda2 --no problems

Then I tried to install PCLinuxOS on hda2 -- install failed -- error message said "can't copy files to new root"

Then I decided to attempt again at a later date and return my computer back to normal.

ran g-parted live cd again removed hda2 and resized hda1 -- no problems

Rebooted machine -- GRUB loads, Xubuntu shows on screen with progress bar

Some message flashes underneath the progress bar (too fast for me to read)

Computer then boots to a shell login -- does not recognize my login or password -- I can however log in as root

I them am left with a prompt something like this:
    PcLinuxOS ~$]

Through the shell I cannot find any of my files. Probably because I am not looking in the right place.

I can however find everything when using a live cd.

There are two vmlinuz files and two initrd.img files in the root directory one of each has .old on the end (might be important)

Any help is appreciated, I bit off more than I could chew. 

Also,is there any way to gain root access to the file system via Live CD GUI?

I don't know what livecd you have, but from a run command type this into it: **gksu nautilus**

You might want to type **mount** while using pclinuxos to find out what's mounted. that's why you can see the files under livecd and not pclinuxos.

---

### Post by 123456789123456789123456 on 2009-06-08
I think I know what happened.
For some reason, pclinux attempted to install in the same partition that xubuntu is on.
if you are able to, under the live cd, backup all your personal data, from the xubuntu disk.  onto another disk, or flash drive so forth.
keep one of the files you said was duplicated.  on one of each, rename it, with the same name, but remove the .old from it.  Try rebooting the machine.
See if xubuntu is able to load.
the simplest way to do a dual boot with pclinux, that I know of, is to have pclinux install on a clean disk, with no xubuntu on it.  Then use xubuntu cd, to automatically resize the drive, and install.  it should create at least 1 new partition, leaving the swap partiton created by pclinux alone, if it created one, if it did not, ubuntu will create one.  you will end up with 3 partitons, the last partiton being swap.
you may have to back up your personal data, and do a clean wipe of the disk, and follow those instructions on dual booting.

---

### Post by stuart.reinke on 2009-06-09
> **123456789123456789123456 said:**
> I think I know what happened.
For some reason, pclinux attempted to install in the same partition that xubuntu is on.
if you are able to, under the live cd, backup all your personal data, from the xubuntu disk.  onto another disk, or flash drive so forth.
keep one of the files you said was duplicated.  on one of each, rename it, with the same name, but remove the .old from it.  Try rebooting the machine.
See if xubuntu is able to load.
the simplest way to do a dual boot with pclinux, that I know of, is to have pclinux install on a clean disk, with no xubuntu on it.  Then use xubuntu cd, to automatically resize the drive, and install.  it should create at least 1 new partition, leaving the swap partiton created by pclinux alone, if it created one, if it did not, ubuntu will create one.  you will end up with 3 partitons, the last partiton being swap.
you may have to back up your personal data, and do a clean wipe of the disk, and follow those instructions on dual booting.
I had the same suspitions. Problem is that I can't delete either vmlinuz or initrd.img and rename the old ones because they are read only. (even as root).

Everything was backed up before, will probably do a clean install. (was thinking of trying the new ext4 file system anyway)

---

