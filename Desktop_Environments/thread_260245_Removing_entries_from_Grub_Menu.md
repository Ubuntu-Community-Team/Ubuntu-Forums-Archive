---
title: "Removing entries from Grub Menu"
date: 2006-09-18
forum: Desktop Environments
---

### Post by MystaMax on 2006-09-18
Hello, I've been running Ubuntu since the release of 6.06, and have installed numerous kernel updates provided via ubuntu system updates. I believe I have about 6 available kernels to choose from @ startup. Then, theres a second entry for each kernel labeled as recovery mode. So that makes this list very long. 

Am I going to mess anything up by removing these? Is it necessary to keep these older kernels on this list? If not, **how do I remove older entries?** Do I need to provide a list of the kernels I have available? Thanks in advance!

---

### Post by jd65pl on 2006-09-18
Try:

```
sudo gedit /boot/grub/menu.lst
```

comment out the bits you don't need with "#"

Thanks

J

---

### Post by MystaMax on 2006-09-18
Thanks for the quick reply jd65pl. So, if my system is working the way I like it @ this time, it safe to remove all older kernels? Is leaving the recovery kernels a security risk? Or is it more helpful to leave for a beginner for easy repair?

---

### Post by bswilson on 2006-09-18
No, go right ahead.  I recommend this procedure in case you tend, like me, to screw up from time to time:

Step 1. Back up your good grub configuration.
```
$ sudo cp /boot/grub/menu.lst ~/menu.lst.BAK
```

Step 2. Edit the list as root so you can save the changes.
```
$ gksudo gedit /boot/grub/menu.lst
```

Step 3. Make your changes, save, reboot.

---

### Post by ronmarley1 on 2006-09-18
Another option would be to go into Synaptic and search for the kernal versions you want to remove.  I'm downloading 2.6.15-27-386 now, so it looks like there's another to add to the list.  It's been my practice to remove all but the current one and the next previous.  Then, if need be, as the other poster suggested, you can boot to the older kernal if you have problems.

---

### Post by Tomosaur on 2006-09-18
I only have 1 kernel displaying, but I have a couple installed for safety reasons. You can set Grub to show however many kernel variations you want, but it isn't always reliable, since it only goes by the kernel name, and whichever has the highest number. The script in my sig should make this very easy for you, or you can just alter /boot/grub/menu.lst by hand. You will need to run 'update-grub' after altering the number of kernels to be shown.

---

### Post by jd65pl on 2006-09-18
I would recommend backing the file up like the other guy said and commenting out the bits you don't want. That way you can always restore the settings you changed

Thanks

J

---

### Post by MystaMax on 2006-09-18
Wow, thanks for all the quick responses, very helpful!

> **ronmarley1 said:**
> Another option would be to go into Synaptic and search for the kernal versions you want to remove.  I'm downloading 2.6.15-27-386 now, so it looks like there's another to add to the list.  It's been my practice to remove all but the current one and the next previous.  Then, if need be, as the other poster suggested, you can boot to the older kernal if you have problems.


This option also seems like it would save disk space for those that need the extra space.

Thanks again guys, I'll change the title to SOLVED.

---

### Post by MKR. on 2006-09-18
A related question:

If I somehow wreck GRUB's config file, will the system be unbootable and need to be fixed via a livecd, or does GRUB have the ability to recover from mistakes in editing its config file?

---

### Post by jd65pl on 2006-09-18
Put it this way its best to always make a back up of this file before making alterations. It is quite possible that you could make your system unbootable by editing this file. 

I have been able to restore grub from a live cd many times though because of various issues.

Thanks

J

---

