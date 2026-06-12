---
title: "ntfs-3g: Only 1 of 2 ntfs p's shows in Places and on Desktop"
date: 2006-08-01
forum: Desktop Environments
---

### Post by msandersen on 2006-08-01
Hi
I installed NTFS-3G yesterday from this [HowTo]("http://www.ubuntuforums.org/showthread.php?t=217009"), and it works great from what I can tell. 
However, whereas I've mounted 2 NTFS partitions, Windows and Data2, and they're both accessible from Nautilus, Ubuntu only shows the first one on the Desktop, as well as under Places. If you go to Computer, Data2 has a different icon, and whereas clicking on Windows will open it as expected, clicking on Data2 (which is mounted and available from /media/Data2) will show the error 
"Unable to mount the selected volume
Mount: according to mtab, /dev/fuse is already mounted on /media/data2 
mount failed"
I don't know if the difference in case is significant, ie Data2 vs data2 (the first is correct).
I've mounted the Windows partition to **/media/Windows** and the Data partition to **/media/Data2**. They are both owned by Root with full permissions (umask 0).

fstab:
```
/dev/hda1  /media/Windows  ntfs-3g  silent,umask=0,locale=en_AU.UTF8  0  0
/dev/hda8  /media/Data2    ntfs-3g  silent,umask=0,locale=en_AU.UTF8  0  0
```

mtab:
```
/dev/fuse  /media/Windows  fuse  rw,nusuid,nodev,noatime,default_permissions,allow_other  0  0
/dev/fuse  /media/Data2  fuse  rw,nusuid,nodev,noatime,default_permissions,allow_other  0  0
```

Now, is the fact that 2 pertitions are trying to mount to /dev/fuse in mtab the problem so that only the first shows, ie a Fuse bug, or an Ubuntu/Debian problem, considering it is reachable from Nautilus and can be saved to just fine from applications by browsing to it?

Is there a fix for this?

---

### Post by rb32 on 2006-08-01
I do have the same problem. I figured also out that the read-only driver displays the partition labels. ntfs-3g seems not to be able to do this.Hope there will be a solution.

In the meanwhile I will mount my Windows system partition read-only and only the Data partition read-write.

I will use this as workarround.

---

### Post by givré on 2006-08-01
The explication is in the threat, quite a common problem. I'll put it in the main page
[QUOTE=givré]Unfortunatly, there is no solution for this problem. ntfs-3g use fuse to mount partition. The system refer to /dev/fuse which refer to all the partition it control... So all for the system, it's like that all your NTFS partition are /dev/fuse. If you do 'more /etc/mtab' in a terminal, you will see it. The consequence is that gnome can only show one (the first one) on the desktop and on place>cumputer.
If you want to be able to access them quikly, you can make a bookmark in nautilus, or you could also mount you partition in your home.
Ex:you can make a directory call windows in your home and change the mount point to /home/<your username>/windows in /etc/fstab.
You don't need to mount them in /media, if i made the HowTo like that it's only because the partition mounted in /media are show on the desktop, and for newbie, it's quite important to see them, just like windows do it.
Hope that will help.[/QUOTE]

---

### Post by msandersen on 2006-08-01
It's not just my system then, but a known problem; hopefully known by the ntfs-progs developers, and hopefully some sort of fix is in the works. But then, ntfs-progs has been around a while, and presumably it's been a problem with the old ntfsmount version, at least in Gnome, so it probably has low priority. So I take it there's no fix or workaround at present.

For now, I reversed the order of the Windows and Data2 mount points in fstab, so it's the Data partition that shows on the Desktop and in Places. Most of what I want from the main Windows partition is in the My Documents folder anyway, so I was gonna make a symlink in my home dir to it anyway. I was also planning to have a symlink to the Data2 partition in there as well.
I just want it to work as well and look as neat as it can. Linux still has some catching up to do in general, though NTFS **is** a foreign file system.

Now I have Data1 (ext3) and Data2 (ntfs) showing on the Desktop and in Places. 

From what I read in the ntfs-progs mailing list, the developer who made ntfs-3g wants it to be a separate utility to eventually replace the old one; he's unhappy with the confusing syntax of the old one (ntfsmount for the terminal, ntfs-fuse in fstab), and he feels it represents the new generation of NTFS driver. But it's left up in the air while he's away on his adventure holiday. Some bug fixing and much more optimisation is left to do. Other developers expressed interest in backporting much of it to the main ntfs-progs package, though, and the Kernel module developer is looking at adapting it for the Kernel module, so eventually it may become part of every standard kernel.

---

### Post by givré on 2006-08-01
That's not really an ntfsmount/ntfs-3g bug. It's more the manner that fuse work that lead to that (lot's of that in this sentance :cool: ).
Not sure it could be solve soon. Quite an hard problem.
And about the future of ntfs-3g, they begin to merge it with ntfsmount and they will decide to a name. You can vote on their main page : [www.linux-ntfs.org](www.linux-ntfs.org)

---

### Post by msandersen on 2006-08-01
Well, if the Fuse issue cannot be solved, it seems the only real solution is a proper Kernel module then, though the developer thinks there are advantages of having it in user-space, including not bringing down the system if the driver crashes. It would take a lot longer for a kernel driver to become available, and I figure they'll be a lot more conservative releasing that until it is rock solid. The front page says at least 2007. Which isn't too bad, I guess, especially since nothing has happened with it for a very long time. Ubuntu is a fairly progressive distro, so it should have it in the version immediately after the driver's release.
Being able to show all mounted volumes is important from the whole user-friendliness angle, especially if they want to convert Windows users. Of course, it's only an issue for those dipping their toe in the Linux waters with more than one Windoews partition. I guess most don't by default, except us geeks. But they just might have more than one disk.

---

### Post by msandersen on 2006-08-01
Just for reference, this is what I use now in fstab:
```
/dev/hda7       /media/Data1      ext3       defaults        0       2
/dev/hda8       /media/Data2      ntfs-3g    silent,uid=1000,gid=100,umask=0007,locale=en_AU.UTF8    0    0
/dev/hda1       /media/Windows    ntfs-3g    silent,uid=1000,gid=100,umask=0007,locale=en_AU.UTF8  
```
Data1 is ext3, and I can access it in Windows via the [ext2IFS]("http://www.fs-driver.org/") filesystem driver.
Data2 is NTFS, as is the main Windows partition of course. By placing the Data2 mount first, it is the one showing on the Desktop. I set the UID to mine, and GID to User and Umask to 007, so non-users don't have access.
As for the Windows partition: Since I only really want access to the content of the My Documents folder, I made a symlink in my Home folder:
```
~$ ln -s "/media/Windows/Documents and Settings/mopo/My Documents" "My Documents"
```

---

