---
title: "login resolution"
date: 2006-02-25
forum: Desktop Environments
---

### Post by davidcrickett on 2006-02-25
I cannot set the login screen resolution  to my default 1280x1024, not even using the advice in this thread [http://www.ubuntuforums.org/showpost.php?p=248755&postcount=5](http://www.ubuntuforums.org/showpost.php?p=248755&postcount=5)
I cannot write to the database it seems, not even as root.

The login resolution is much bigger than my default, and it looks ugly.

---

### Post by aysiu on 2006-02-25
Try this: ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst
``` Find the appropriate entry and look for the *kernel* line. Add *vga=794* to it. For example, if your entry looks like this: ```
title           Ubuntu, kernel 2.6.12-10-k7
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.12-10-k7 root=/dev/hda7 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-k7
savedefault
boot
``` change it to this: ```
title           Ubuntu, kernel 2.6.12-10-k7
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.12-10-k7 root=/dev/hda7 ro quiet splash **vga=794**
initrd          /boot/initrd.img-2.6.12-10-k7
savedefault
boot
```

---

### Post by davidcrickett on 2006-02-25
Thanks for the quick reply! Now my ubuntu loading screen is in a much better resolution, but my login screen is still bigger than 1280x1024. I am in Ubuntu Breezy AMD 64bit, if that has any impact on the question?
It says in this place [http://www.ubuntuforums.org/showpost.php?p=248755&postcount=5](http://www.ubuntuforums.org/showpost.php?p=248755&postcount=5)
that the two keys, rate and resolution, is not part of a pair and not writable... :confused:

---

### Post by aysiu on 2006-02-25
Let me make sure I understand what the problem is (though, I may not be able to solve it for you--perhaps someone else will step in): You boot up. During bootup everything's in 1280x1024 until you get to the login screen, at which point it reverts to 1024x768 (or 800x600). Once you log in, it's back to 1280x1024?

---

### Post by davidcrickett on 2006-02-25
No... :) Before your advice, the ubuntu loading screen was in a poor resolution, like the windows loading screen. Now it is smaller, centered, and in a good resolution.

My problem is, that the login screen, the screen you write your login name and password in, the ubuntu thing that comes right after the loading of Ubuntu ;) - is in a BIGGER resolution than my normal desktop screen resolution at 1280x1024. It has a black padding all around, but you can see it's 1600x1200 or something like that, tiny boxes etcetera, and it can't fill out the screen, so I have this high resolution login screen with a 2 centimeter black rim around it.
Hope that explains it better. :)

---

### Post by moffa on 2006-02-28
Don't mean to highjack, but did you find a solution?  If I run "sudo dpkg-reconfigure xserver-xorg" it fixes it but I lose my ati driver installation.  I think it may have to do with ati driver installation.

---

### Post by davidcrickett on 2006-02-28
Yes, I believe it is the ATI driver, too.

---

### Post by BeatBoxRocker on 2006-02-28
You have to modify the file xorg.conf located in /etc/X11. 

Backup: sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
Open the file: sudo gedit /etc/X11/xorg.conf

Go to section Screen and add for every subsection in modes line: "1280x1024"
If there's something higher than 1280x1024 just delete it and keep your highest resolution to the one you want.

Saludos!

---

### Post by davidcrickett on 2006-02-28
I have two screen subsections in xorg.conf, one without modes at all - I put modes "1280x1024" in, and voila! Thank you very much, BeatBoxRocker! :mrgreen:

---

