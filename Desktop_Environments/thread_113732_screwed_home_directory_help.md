---
title: "screwed home directory help"
date: 2006-01-07
forum: Desktop Environments
---

### Post by ae+ on 2006-01-07
hi

i was attempting to add another partition to my ubuntu home directory and although it worked, it also completely wiped my home directory :(

this means i cant access my home directory and whenever i try and run an application or terminal it says it cant because it tries to access the home directory before doing it.

HOWEVER there was a terminal open when the stupidness occurred and it is based in the home directory, and appears to work fine. ie. i can view files when i use 'ls' etc. When i create a new tab in the terminal and move to the home directory there is nothing there (oh no)

any theories or ideas?

i can copy things out of /home/ae 
but i really would love to 'undo' what i have done and restore the home directory to the way it was.

(also - I changed the partition to be located somewhere else)

any help appreciated :)
*sigh*

ae

---

### Post by healychan on 2006-01-07
When you say "add" a partition, do you mean mounting??
What kind of file system is that?? NTFS?? FAT??
Please provide more information;)

I guess the problem is you were trying to mount a filesystem to your home.
Since the home directory contains information about shell, corrupting it will cause inconsistency. Of cause you can browse your home but this "home" is not that "home".

How did you mount that partition?? Did you modify the /etc/fstab file??

---

### Post by Ubluntu on 2006-01-07
I hate to say it, but I think you might be able to reboot and work fine.. If you added the entry to fstab and did a mount -a you should remove the entry from fstab before restarting...

Entry in the fstab or just a mount at command promt, you should be able to unmount it using the unmount command.. try man unmount for specifics, probably the same as mount

If you can see the files from a shell that was open, i bet the files are fine, the OS is just told to look at the other partition, which hopefully you can "undo"

Good luck

---

