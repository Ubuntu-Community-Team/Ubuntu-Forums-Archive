---
title: "symbolic link to '.'"
date: 2009-01-09
forum: General Help
---

### Post by estyles on 2009-01-09
I don't know why I can't figure this out, but I would like to make a symbolic link to '.', that is, to the current directory.  I know that in nautilus, this is usually easy, because you can just browse to one level higher, click on the directory to make a link to and select "Make Link", then copy that link into the directory and rename it.

This won't work for me, because the directory I want to make a link to is the root of the partition it's on.  The partition is mounted at /boot, and if I browse to / and make a link to /boot, it remains a link to /boot, even if the drive is not mounted or is mounted at a different location.  Using "cp -l . boot" (or -s instead) doesn't work.  It says "cp ignores directory ." or something like that...

The problem is that when Grub boots from a separate partition and I try to chainload the Ubuntu /boot partition, it keeps saying "Invalid Device", even though I have setup Grub on that partition (via root (hd0,4), setup (hd0,4)).  I'm guessing that it's because all the kernel images are located at the root of the partition instead of at /boot, and the grub files are at /grub instead of /boot/grub.  It won't load fstab until later on, so the partition isn't mounted at /boot, it's just (hd0,4).  So if I could make "boot" a link to the partition's root, I'm guessing it might work.

Another reason for Grub not being able to boot might be that it cannot boot from an extended partition at /dev/sda5 for whatever reason?  That may be the case, but if I could create a symbolic link to '.', then I could at least test my theory.

---

### Post by mssever on 2009-01-09
> **estyles said:**
> I don't know why I can't figure this out, but I would like to make a symbolic link to '.', that is, to the current directory.  I know that in nautilus, this is usually easy, because you can just browse to one level higher, click on the directory to make a link to and select "Make Link", then copy that link into the directory and rename it.

This won't work for me, because the directory I want to make a link to is the root of the partition it's on.  The partition is mounted at /boot, and if I browse to / and make a link to /boot, it remains a link to /boot, even if the drive is not mounted or is mounted at a different location.  Using "cp -l . boot" (or -s instead) doesn't work.  It says "cp ignores directory ." or something like that...

The problem is that when Grub boots from a separate partition and I try to chainload the Ubuntu /boot partition, it keeps saying "Invalid Device", even though I have setup Grub on that partition (via root (hd0,4), setup (hd0,4)).  I'm guessing that it's because all the kernel images are located at the root of the partition instead of at /boot, and the grub files are at /grub instead of /boot/grub.  It won't load fstab until later on, so the partition isn't mounted at /boot, it's just (hd0,4).  So if I could make "boot" a link to the partition's root, I'm guessing it might work.

Another reason for Grub not being able to boot might be that it cannot boot from an extended partition at /dev/sda5 for whatever reason?  That may be the case, but if I could create a symbolic link to '.', then I could at least test my theory.
You can create a symlink to the current directory thus: ```
ln -s . some_name
```But I'm pretty sure it won't solve your problem.

---

### Post by Joeb454 on 2009-01-09
From what I recall to copy directories, you need to use cp like so: ```
cp -R /path/to/dir /path/to/copy/to
```

---

### Post by jamesisin on 2009-01-09
You might be looking at a permissions issue.  I tried to create a symbolic link on my / directory and received a permission denied error.  I did it on a second drive (over which I have taken ownership) and it worked as expected (though I was technically in /media/DRIVE and not / per se).

You may try letting root run the ln -s . LINKNAME command:

```
sudo ln -s . SlashLink
```

See what that does for you.

---

### Post by estyles on 2009-01-10
Thanks, the "ln -s" command line was what I was looking for.  Tried "cp -s", "cp -l", and "link", but was missing the "ln" command.

I think you're right that it won't solve my problem, but it was bugging the crap out of me that I couldn't do it and knew there had to be a way.  Worth a try, anyway.

Right now, I'm running grub with "configfile (hd0,4)/grub/menu.lst".  It works, but I want to do it with chainloader - it just feels more universal, and less likely to break when Ubuntu updates it's menu.lst automatically.  But oh well, that's a separate problem.

---

### Post by jamesisin on 2009-01-10
I did a little more testing and you can't use . in a ln command.  The resulting link is a link to . and not to the then current directory.

Example:

I create the following link:

ln -s . Pink

I create it in /media/PinkDrive

I test the link and sure enough it clicks through to /media/PinkDrive.

Then I move Pink into another directory, say, /home/[username]/Desktop so that I have access to that other drive.

Now when I test the link it clicks through to /home/[username]/Desktop which is the new . directory.

Instead try:

```
sudo ln -s / SlashLink
```

But that's just a guess...

---

### Post by estyles on 2009-01-11
> **jamesisin said:**
> I did a little more testing and you can't use . in a ln command.  The resulting link is a link to . and not to the then current directory.


That is, in fact, what I want.
If I have /dev/sda5 mounted at /boot, I don't want a link to /boot, I want a link to the current directory in the root of /dev/sda5.

---

### Post by mssever on 2009-01-11
> **estyles said:**
> That is, in fact, what I want.
If I have /dev/sda5 mounted at /boot, I don't want a link to /boot, I want a link to the current directory in the root of /dev/sda5.
That's confusing. If sda5 is mounted on /boot, then a link to sda5's root directory is indistinguishable from a link to /boot. You might as well just make a link to /boot.

If you're wanting to link to the device itself, you'll have to link to /dev/sda5, in which case you get the partition itself and can't access files on it until you mount it somewhere. A symlink can only point to a file that's otherwise accessible (well, you can have a broken symlink, but that's not useful).

---

### Post by estyles on 2009-01-11
> **mssever said:**
> That's confusing. If sda5 is mounted on /boot, then a link to sda5's root directory is indistinguishable from a link to /boot. You might as well just make a link to /boot.

If you're wanting to link to the device itself, you'll have to link to /dev/sda5, in which case you get the partition itself and can't access files on it until you mount it somewhere. A symlink can only point to a file that's otherwise accessible (well, you can have a broken symlink, but that's not useful).

No, no, no.  You answered my question correctly and helped me out, so I have to think you understood at the time...

A link to '.', located in the root of the partition mounted at /boot is not at all indistinguishable from a link to /boot.  If the drive is not mounted at /boot (like when Grub boots up, looking for (hd0,4)/boot, or if it were mounted at a different point), the link to '.', which you helped me figure out how to create, is totally different from a link to /boot or a link to /dev/sda5.

If I mount the drive at /mnt/tmp for whatever reason, then the link to '.' will still point to the root of /dev/sda5, which would now be located at /mnt/tmp.  A link to /boot will point at /boot.

---

### Post by mssever on 2009-01-11
> **estyles said:**
> No, no, no.  You answered my question correctly and helped me out, so I have to think you understood at the time...I understood the specific question I answered. I didn't understand the full post.

> A link to '.', located in the root of the partition mounted at /boot is not at all indistinguishable from a link to /boot.  If the drive is not mounted at /boot (like when Grub boots up, looking for (hd0,4)/boot, or if it were mounted at a different point), the link to '.', which you helped me figure out how to create, is totally different from a link to /boot or a link to /dev/sda5.

If I mount the drive at /mnt/tmp for whatever reason, then the link to '.' will still point to the root of /dev/sda5, which would now be located at /mnt/tmp.  A link to /boot will point at /boot.OK. That's true, but I don't understand why it would be useful. Consider this sequence of commands: ```
cd /boot
sudo ln -s . boot_root
sudo mv boot_root /etc
ls /etc/boot_root
```which would result in a listing of /etc, not /boot, because the symlink points to . (i.e., the directory in which it is currently located).

So, to reference the root of your sda5, you have to know where it's mounted, which means that for a partition mounted on $x, referencing $x/boot_root is identical in meaning to referencing $x. So you've only added an additional component to your filename. To be more specific, referencing /boot/boot_root and /boot are essentially the same. Ditto for /mnt/tmp/boot_root and /mnt/tmp. And referencing /boot/boot_root won't get you /mnt/tmp.

What am I missing here?

---

### Post by estyles on 2009-01-11
> **mssever said:**
> So, to reference the root of your sda5, you have to know where it's mounted, which means that for a partition mounted on $x, referencing $x/boot_root is identical in meaning to referencing $x. So you've only added an additional component to your filename. To be more specific, referencing /boot/boot_root and /boot are essentially the same. Ditto for /mnt/tmp/boot_root and /mnt/tmp. And referencing /boot/boot_root won't get you /mnt/tmp.

What am I missing here?

I still haven't tested to see if my theory is true, but my theory was that when you use "root (hd0,4) chainloader +1" in a grub menu, I think it is looking for files to be at "(hd0,4)/boot/grub/".  Since that partition is normally (after bootup) mounted at "/boot", the kernel images are at (hd0,4)/ and the grub files are at (hd0,4)/grub/.  Therefore, I want (hd0,4)/boot/grub to contain the same files as (hd0,4)/grub, without just copying them and having two copies of everything to maintain.  Creating a link to /boot would work fine when the partition is mounted, but when grub is running, it is not mounted at /boot.

Now I haven't rebooted since then to check if this helps or not, but thanks to your help, I can at least try it.  Now considering that I set up the drive using grub root(hd0,4) setup(hd0,4), and it was able to find the grub/stage1 files on (hd0,4) even *without* the link, and said that it was setup successfully - well, that leads me to believe that this isn't actually going to work, but like I said, it's worth a try.  But I can't think of any other reason why grub would return an Error 12: Invalid Disk (or something like that) on a partition that I have setup grub on.

---

### Post by jamesisin on 2009-01-11
Is there a way to manually edit a link once it has been created?  I tried opening it in GEdit (overly optomistic?) and that went nowhere.  And of course the Properties dialog for a link is next to useless.

---

### Post by mssever on 2009-01-11
> **estyles said:**
> I still haven't tested to see if my theory is true, but my theory was that when you use "root (hd0,4) chainloader +1" in a grub menu, I think it is looking for files to be at "(hd0,4)/boot/grub/".  Since that partition is normally (after bootup) mounted at "/boot", the kernel images are at (hd0,4)/ and the grub files are at (hd0,4)/grub/.  Therefore, I want (hd0,4)/boot/grub to contain the same files as (hd0,4)/grub, without just copying them and having two copies of everything to maintain.  Creating a link to /boot would work fine when the partition is mounted, but when grub is running, it is not mounted at /boot.
OK, I think I understand now what you're trying to accomplish. I have no experience in running Grub in a way other than the default, so I don't know whether that will work. If it doesn't, it may be that Grub won't follow symlinks. In that case, you can try making hard links (ln target new_name) to the individual files. You can't make a hard link to a directory, and hard links can't cross partitions. But they're indistinguishable from standard files. If you delete the "target," the file is still available at the other name.
> **jamesisin said:**
> Is there a way to manually edit a link once it has been created?  I tried opening it in GEdit (overly optomistic?) and that went nowhere.  And of course the Properties dialog for a link is next to useless.
Just delete the symlink and re-create it. You can't open a symlink in a regular editor, because the editor will open up the target instead. That's the way symlinks work. They're not equivalent to Windows' shortcuts (see .desktop files for the equivalent). It's probably possible to write a tool to directly edit symlinks, and indeed such a tool might be available, but it's just as easy to delete the link and re-create it.

---

### Post by jamesisin on 2009-01-12
Yeah, I usually just rebuild them.  I was just wondering.  Thanks.

---

### Post by dcstar on 2009-01-14
> **estyles said:**
> I still haven't tested to see if my theory is true, but my theory was that when you use "root (hd0,4) chainloader +1" in a grub menu, I think it is looking for files to be at "(hd0,4)/boot/grub/".  Since that partition is normally (after bootup) mounted at "/boot", the kernel images are at (hd0,4)/ and the grub files are at (hd0,4)/grub/.  Therefore, I want (hd0,4)/boot/grub to contain the same files as (hd0,4)/grub, without just copying them and having two copies of everything to maintain.  Creating a link to /boot would work fine when the partition is mounted, but when grub is running, it is not mounted at /boot.


You do not understand the difference between an OS filesystem and the "raw" disk structure that Grub works with.

"root (hd0,4) chainloader +1" just instructs Grub to boot of a specific partition on a specific drive, and Grub has no concept of fancy things like symbolic links at that stage (it just passes the job over to whatever OS boots off that partition).

You can see where Grub is instructed to load specific files in the various other boot entries on an Ubuntu system, and they are all absolute paths (probably for a good reason).

---

