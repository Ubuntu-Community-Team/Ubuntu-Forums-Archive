---
title: "Grub2 - Removing old Kernels"
date: 2009-05-07
forum: General Help
---

### Post by bacardiandwatermelon on 2009-05-07
I've just installed Grub2, everything seams fine but editing the menu.lst doesn't remove old kernels anymore. I tried editing the grub.cfg file, but when update-grub is run it just rebuilds the cfg file. I've tried looking on the Grub2 wiki but I couldn't find much. Any ideas?

---

### Post by nawitus on 2009-05-07
[http://www.pendrivelinux.com/how-to-remove-old-kernel-images/](http://www.pendrivelinux.com/how-to-remove-old-kernel-images/)

It's safe to run 'sudo update-grub' afterwards too.
EDIT: Oh, it's grub2. Don't know if these apply.

---

### Post by bacardiandwatermelon on 2009-05-07
Ahh I'm such an idiot :-P

Removing linux-image-2.6.xx-xx-xxx from synaptic and then running sudo update-grub removes the old kernels. Cheers.

---

### Post by sphyg04 on 2009-12-06
> **bacardiandwatermelon said:**
> Ahh I'm such an idiot :-P

Removing linux-image-2.6.xx-xx-xxx from synaptic and then running sudo update-grub removes the old kernels. Cheers.

Works Great! AWESOME! Thanks

---

### Post by atleastitsnotcrack on 2010-04-03
Great! Very easy to do and better then just making it so they appear to not be there when they are.

---

### Post by kesoapa on 2011-03-25
Searched for an option to remove entries from the grub-menu and stumbled upon this thread. This pushed me in the right direction. Thanks for the help!

I did this on my Ubuntu server, listing the kernels I've got installed by running
```
sudo aptitude search linux-image-2.6 | grep "i "
```Note the spaces after the i in grep i. This to list only the installed kernels.

After getting to know which kernels are installed I purged all but the initial kernel from install-time of Ubuntu server 10.04, and the two latest ones.
For me that would be
```

sudo aptitude purge linux-image-2.6.32-27-server
sudo aptitude purge linux-image-2.6.32-28-server

```Last, to rebuild the grub-menu
```
sudo update-grub
```Hope this can help someone who use aptitude in a server-environment.

---

