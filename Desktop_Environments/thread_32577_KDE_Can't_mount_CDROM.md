---
title: "KDE Can't mount CDROM"
date: 2005-05-08
forum: Desktop Environments
---

### Post by wwwolf on 2005-05-08
MOUNTING:   All I know is that I use to be able to put a cd in the drive and the cd-icon would show up on the desktop. I would then click to open it or right click and select mount and the icon would then be replaced by the mounted-cd-icon. I could then browse all of the files on the cd, rightclick and select eject and the cd would unmount and eject.

Now, I put the cd in the drive, the cd-icon shows up, I click on it and It refuses to mount and tells me some proccess died unexpectedly (but it won't tell me which one). Even though KDE refuses to recognize that dev/hdc is mounted, it is in fact really mounted because I can browse the files from /cdrom.

UNMOUNTING:   Now that the CD is pseudo-mounted, I can see the files but when I am ready to unmount it KDE can't do it because it thinks it was never mounted in the first place. I enter the shell, and do 'sudo umount -l /dev/hdc' to unmount it but I still can not eject it until I do 'sudo eject /dev/hdc'
   The problem is that the old-unmounted-CD-icon is still on the desktop and when I am ready to put in a new CD the desktop will not recognize it and 'sudo mount /dev/hdc' returns without any errors but I cannot browse the files on the second CD.

In order to veiw the second CD I have to reboot the computer. (In linux this concept is almost unheard of)

I wonder if this has anything to do with the KDElibs-data update problem.

I wish at least that I knew of a command that would tell the computer 'what you think is in /dev/hdc is wrong so reinitialize yourself so you will display the correct data' which is probably what the rebooting does. 

I know that /ect/fstab is correct because my laptop (never updated) has the same fstab and does not do this behavior.

If I could at least find out a way not to have to reboot the computer I will be temporarily happy until the bug is fixed (if it is a bug).

I would appreciate any help,
Thanx,

wwwolf

---

