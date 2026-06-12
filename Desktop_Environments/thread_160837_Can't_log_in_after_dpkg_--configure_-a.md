---
title: "Can't log in after dpkg --configure -a"
date: 2006-04-15
forum: Desktop Environments
---

### Post by entryname on 2006-04-15
Attempted install of libc6-dev for compilers. It finished the download but during the install it reported some kind of problem with dpkg, it was interrupted or something, and that I would have to do dpkg --configure -a to fix it manually. So I did exactly that. It appeared to say it was configuring libc6-dev and didn't report any error.

After that, my free space shrank to zero. Tried reboot, but couldn't get back in as it said it couldn't create my GDM file. Tried alternate kernel, no difference. I can get to a recovery prompt and create a directory on the hard disk from it, so the disk must be OK, but I don't know what else to do, so I guess I'll have to give up and reinstall, or maybe give up on Ubuntu, or maybe just give up on Linux.

Any helpful suggestions at all about what could have gone wrong, and if there is any way to fix it from a recovery prompt?

This keeps happening with linux. It will run for a while, then huge crash and I have to rip it off. Doesn't seem to matter which distro, some are better than others but in the end they all let me down. I do feel thoroughly demoralised here. I'm wondering if maybe Linux is just not as good as I thought it was and if I should try again in another ten years. :(

---

### Post by az on 2006-04-15
[QUOTE=entryname]Attempted install of libc6-dev for compilers. It finished the download but during the install it reported some kind of problem with dpkg, it was interrupted or something, and that I would have to do dpkg --configure -a to fix it manually. So I did exactly that. It appeared to say it was configuring libc6-dev and didn't report any error.

After that, my free space shrank to zero. Tried reboot, but couldn't get back in as it said it couldn't create my GDM file. Tried alternate kernel, no difference. I can get to a recovery prompt and create a directory on the hard disk from it, so the disk must be OK, but I don't know what else to do, so I guess I'll have to give up and reinstall, or maybe give up on Ubuntu, or maybe just give up on Linux.

Any helpful suggestions at all about what could have gone wrong, and if there is any way to fix it from a recovery prompt?

This keeps happening with linux. It will run for a while, then huge crash and I have to rip it off. Doesn't seem to matter which distro, some are better than others but in the end they all let me down. I do feel thoroughly demoralised here. I'm wondering if maybe Linux is just not as good as I thought it was and if I should try again in another ten years. :([/QUOTE]

You ran out of disk space.

You need to boot a live cd, mount your install partition and delete some stuff.  Try clearing the /var/cache/apt/archive directory

---

### Post by Ramses de Norre on 2006-04-15
If you can get to a recovery prompt you should be able to clear out some space from there too.
Do apt-get clean
To reboot do init 6

---

### Post by towsonu2003 on 2006-04-15
you can check the free space with 
df -h (if from live cd, mount partitions first -if you need help with mounting partitions, post the output of sudo fdisk -**l**)

try sudo dpkg-reconfigure xserver-xorg and go tru the "wizard". try starting X with startx afterwards. 

check your log file for X with
cat /var/log/Xorg.0.log | grep EE | less #check for errors
cat /var/log/Xorg.0.log | grep WW | less #check for warnings

boot from live cd and browse thru the (mounted) filesystem (/media/something/)  to see what might be the files that take too much space (in nautilus, right click on a folder and choose "properties", check the size). most places that might screw your space are under /var (in livecd: /media/something/var after mounting partitions).

to reboot: sudo reboot (or anything above posters suggest)

---

### Post by entryname on 2006-04-16
OK this is what seems to have happened. backup2l (backup tool) had been set to back up to /home/<user>/Backup and had created around 3GB of successive backups. I'm not clear on why, especially given that I had only run it I think once or maybe twice, but it does appear that it was making differential backups apparently unaided by me, which appears to amount to no set limit to disk space occupied. 

Doing df -h to my great surprise did indeed show 9.0GB out of 9.1GB full. (There was also a clue when it reported on the disk state during the boot sequence as most of the blocks seemed to be full, but I missed that.) Deleted all the backup files, rebooted, I'm back in :) So what I need to try and do now is move the backups to the second hard disk, and find some way of limiting how much space they take up. 

At this precise moment I'm not sure how I configure backup2l. In any case it's not quite what I wanted. I was really after something that would reload the lot from CDs, but I couldn't get mondo and mindi to install properly.

On reading other posts, I did remove .ICEauthority and .Xauthority, hopefully that won't have done any harm :-/

Sorry I threw a wobbly about Linux earlier .... its just that these scares unnerve me :-/ I can hear someone saying that at least I GOT a recovery prompt, whereas windows might not have been so obliging. If the laptop I'm on now crashes badly, unless system restore or suchlike fixes it, I'd have to reload the system from bootable DVDs. This is why I was after something like that for Linux, because I'm used to thinking that way.

---

### Post by towsonu2003 on 2006-04-16
[QUOTE=entryname]its just that these scares unnerve me :-/ [/QUOTE]
I couldn't agree more: getting locked out of X scares the hell out of me... and happens once in a while due to my own mistakes :) I'm just so glad they invented this "LiveCD" concept ;)

---

