---
title: "Help with a mount command...  and then some!"
date: 2006-08-18
forum: Desktop Environments
---

### Post by musther on 2006-08-18
As anyone who read a recent post I made will know I'm trying to slap together some useful scripts for checking filesystems so that people don't have to sit through the automatic fsck on boot every 30 times.  

I was hoping people would help in this, but they don't seem to want to, so I'm just muddling through on my own.

What I need right now is a command to remount partitions as read only, I believe the command to remount / should be something like this:

```
mount -o remount,ro / -f
```

maybe I'm completely wrong, but this doesn't seem to work, after issuing it I still have full access to / (as root of course).

My aim is pehaps to be able to remount all partitions as read only, maybe with something like this:

```
mount -a -o remount,ro
```

So that I can then check them all with fsck.  

On a related note, what options should I use with fsck (to offer a similar check to the routine one which happens every 30 mounts).  

Finally I'm hoping to wrap this all with some nice zenity graphics, and hopefully a zenity progress bar which shows something sensible (not sure how easy that'll be).  

If anyone is interested in helping, please offer.  If not, please at least answer the questions I have above.

Thanks

---

### Post by murataht on 2006-08-18
> **musther said:**
> 
What I need right now is a command to remount partitions as read only, I believe the command to remount / should be something like this:

```
mount -o remount,ro / -f
```

maybe I'm completely wrong, but this doesn't seem to work, after issuing it I still have full access to / (as root of course).

I am not an expert of mount, but i want to learn it. so, i checked the man file, and for the above code, it seems -f option is not correct. (i am not sure). check this out:
>  -f     Causes  everything to be done except for the actual system call; 
              if it’s not obvious, this ‘‘fakes’’ mounting  the  file  system.
              This  option is useful in conjunction with the -v flag to deter&#8208;
              mine what the mount command is trying to do. It can also be used
              to add entries for devices that were mounted earlier with the -n
              option.

hope others can join this discussion.

---

### Post by musther on 2006-08-18
I thought -f was force.  Oh well, it doesn't work without -f either!

Yes, I hope somebody who really knows the ins and outs of 'mount' will help (us both).

---

### Post by ciscosurfer on 2006-08-18
If I'm understanding you correctly, you can try this```
mount -r -o remount /
``` or you can add the following to you options line within your /etc/fstab```
errors=remount-ro
```Otherwise, this might help with what you are doing >> [http://www.gnu.org/software/libc/manual/html_node/Mount_002dUnmount_002dRemount.html](http://www.gnu.org/software/libc/manual/html_node/Mount_002dUnmount_002dRemount.html)
and well as this >> [http://gentoo-wiki.com/HOWTO_Read-only_root_filesystem](http://gentoo-wiki.com/HOWTO_Read-only_root_filesystem)

---

### Post by dannyboy79 on 2006-08-18
I am sure how you will accomplish this without booting the machine up with a live cd or what not. You can't check any filesystem when it is mounted at all, whether it's mounted read only or not! I've read that fsck will royally screw up any data on a partition that it checks if that partition is mounted hence why fsck runs every 30 boots BEFORE it actually mounts everything. I am however a newbie so I could be wrong.

---

### Post by musther on 2006-08-18
I was under the impression it could be done mounted as read only, I'll have to have another look.

---

### Post by musther on 2006-08-18
I suppose the easiest way to do this would be to issue the command which makes fsck check the partitions on next boot, then reboot the system and do something so that when the machine finishes booting it will shut dows.  THe final product script will work like this:

1 Issue fsck reboot command thingy
2 reboot
3 boot fsck of all partitions
4 boot completed
5 system shutdown and halt

In this configuration the script will work as a 'scan disks and shut down' command.

So, does anybody know the command to make fsck kick in on next boot, or do I have to dig around the forums?

Also, how can I get the script to make the machine shut down and halt after the next boot, put something in the init scripts?

Thanks

---

### Post by ciscosurfer on 2006-08-18
This will help with your question: [http://ubuntu.wordpress.com/2005/10/12/tuning-the-filesystem-check-at-bootup/](http://ubuntu.wordpress.com/2005/10/12/tuning-the-filesystem-check-at-bootup/)

---

### Post by musther on 2006-08-18
Thanks for that, it's exactly what I needed, now all I need to know is how to make the machine shut down to halt after it has booted, I imagine it's fairly easy, I just don't know how.

---

