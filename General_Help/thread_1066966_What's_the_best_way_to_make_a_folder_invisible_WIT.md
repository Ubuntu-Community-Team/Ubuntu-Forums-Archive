---
title: "What's the best way to make a folder invisible WITHOUT USING A DOT . PERIOD?"
date: 2009-02-11
forum: General Help
---

### Post by tomstealthports on 2009-02-11
Okay, I have an internal NTFS data partition which Windows just has to place "System volume information" and "Recycler" folders on.  So, how do I make these invisible in Ubuntu without using a period?  I am assuming here that it's not practical to rename "system volume information" as ".system volume..." because then Windows will just make another folder without the dot probably next time I'm on Windows.  

Any ideas?

---

### Post by Slim Odds on 2009-02-11
ext2/3 does not have an attribute to "hide" directories likes some other file systems.

---

### Post by Tibuda on 2009-02-11
> **Slim Odds said:**
> ext2/3 does not have an attribute to "hide" directories likes some other file systems.

Yeah, but he is using NTFS

---

### Post by tomstealthports on 2009-02-11
Hmm.  I think system volume information only turns up when you turn on system restore on a drive.  I could just turn it off and the recycle bin on that drive I guess, but I don't really want to do that, plus there's other windows-specific folders that have a mind of their own I'd like to hide.  Doesn't look like I can, though!

---

### Post by geirha on 2009-02-11
This is not quite what you're asking, but I think it could be a viable option for you.

I'll assume that ntfs drive is currently mounted at /media/windows and has an entry in /etc/fstab.

1. Create a new folder on your NTFS. For example /media/windows/linux
```
mkdir /media/windows/linux
```

2. Create a new mount-point for it "hidden" away somewhere other than /media. I'd go for /mnt/windows
```
sudo mkdir /mnt/windows
```

3. Unmount the NTFS partition ```
sudo umount /media/windows
```

4. Edit /etc/fstab and change the mount-point for that ntfs partition from /media/windows to /mnt/windows. And in addition, add a new line:
```
/mnt/windows/linux /media/windows none bind 0 0
```

5. Mount the new entries
```
sudo mount -a
```

/media/windows should now be the same as /mnt/windows/linux ... an empty folder ... so far.

---

### Post by Slim Odds on 2009-02-11
> **danielrmt said:**
> Yeah, but he is using NTFS

That's true, but linux must map NTFS attributes into it's own. And it does not have the concept of a "hidden file" bit.

---

### Post by dcstar on 2009-02-12
> **Slim Odds said:**
> That's true, but linux must map NTFS attributes into it's own. And it does not have the concept of a "hidden file" bit.

That's right, it is not the filesystem type that determines if something is hidden or not, it is the O/S accessing the filesystem and then deciding to support any attributes like that.

Linux uses the "." as the hidden filesystem attribute on its native filesystems, other OSs use different methods and Linux may or may not support those methods if it connects to those filesystems.

It would probably be better if Linux supported (and gave you the option to use) the "Hidden" attribute on any non-Linux filesystem it mounts - that should probably go on a wish-list somewhere.......

---

### Post by mcduck on 2009-02-12
If you want, you can just create a file called ".hidden" and list the directories/files you wish to hide in that file, one on each line. (The .hidden file and files/directories you wish to hide must be in the same place, you can't define paths in the .hidden file)

This will not hide anything from CLI, but most graphical file browsers in Linux will use it.

So, in your case, you'd create a ".hidden"file in the root of that drive, and then add "System Volume Information" and "Recycler" to that file.

---

### Post by tomstealthports on 2009-02-12
Great bunch of replies there guys, I thought this thread would have died a miserable death overnight!

McDuck, I think you may have won the suggestion contest.  So, I just make a .hidden file on the root of the data disk with the names of the folders I want to hide in that file?  (Goes off to try...)

Woohoo!  What a great solution!

---

### Post by mcduck on 2009-02-12
> **tomstealthports said:**
> Great bunch of replies there guys, I thought this thread would have died a miserable death overnight!

McDuck, I think you may have won the suggestion contest.  So, I just make a .hidden file on the root of the data disk with the names of the folders I want to hide in that file?  (Goes off to try...)

Woohoo!  What a great solution!

yeah, exactly. You can put a ".hidden" file in  every directory where you have something you wish to hide without renaming it. The only limitation is that .hidden file must be in the same location as the things it hides.

---

### Post by tomstealthports on 2009-02-12
Not a very big limitation, though.  Certainly not when compared with my fstab editing capabilities anyway!

---

