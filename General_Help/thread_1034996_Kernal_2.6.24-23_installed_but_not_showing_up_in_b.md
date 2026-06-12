---
title: "Kernal 2.6.24-23 installed but not showing up in boot menu"
date: 2009-01-09
forum: General Help
---

### Post by Green_Star on 2009-01-09
Hi,

My ubuntu 8.04, just installed with kernel 2.6.24-23 but it is not showing up in my boot menu. How do I enable it so that my ubuntu boots in to that kernal, I checked my menu.lst it is not there. Synaptic package showing as it is installed.

---

### Post by MeURi on 2009-01-09
I have the same kind of problem: whenever I got a new kernel installed, I have to manually edit the menu.lst in the grub folder.

Still trying to understand why... :-(

---

### Post by Green_Star on 2009-01-09
How do you add this to menu.lst? just like copy and paste lines of existing kernel and modify the kernel number?

---

### Post by _sleeper on 2009-01-09
you can use qgrubeditor for an easy edit of your menu.lst, otherwise you should do

```

gksu nano /boot/grub/menu.lst

```

then you should manually:
a) if you want to have the option to boot from both kernels add at the end of the Ubuntu options lines like this:

```
title Ubuntu 8.04.1, kernel 2.6.24-23-general
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=82ad6ba0-7108-4bca-8d86-e020ba6d9201 ro quiet splash
initrd /boot/initrd.img-2.6.24-23-generic
quiet
```

b) if you want to boot only from the new one, the only thing you should change is to replace 21 with 23, if let's say your previous kernel was 2.6.24-21 and make it 2.6.24-23, since all kernel images are stored in the /boot directory.

EDIT: don't forget to make a copy of your current menu.lst, in case something goes wrong!

---

### Post by Green_Star on 2009-01-09
> **_sleeper said:**
> you can use qgrubeditor for an easy edit of your menu.lst, otherwise you should do

```

gksu nano /boot/grub/menu.lst

```

then you should manually:
a) if you want to have the option to boot from both kernels add at the end of the Ubuntu options lines like this:

```
title Ubuntu 8.04.1, kernel 2.6.24-23-general
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-23-generic root=UUID=82ad6ba0-7108-4bca-8d86-e020ba6d9201 ro quiet splash
initrd /boot/initrd.img-2.6.24-23-generic
quiet
```

b) if you want to boot only from the new one, the only thing you should change is to replace 21 with 23, if let's say your previous kernel was 2.6.24-21 and make it 2.6.24-23, since all kernel images are stored in the /boot directory.

EDIT: don't forget to make a copy of your current menu.lst, in case something goes wrong!

Thanks .

---

### Post by MeURi on 2009-01-10
The question remains: why it's not done automatically? Does anyone have any clues? On my previous Ubuntu installation it worked flawlessly :-(

EDIT: I could have searched the forums better... [thread=1003779]here[/thread] the problem seems the same, and it has been fixed by purging and reinstalling GRUB, then doing a grub-update

Hope this solves the issue for us

---

### Post by _sleeper on 2009-01-10
actually, when i update the kernel a window pops and asks me if i want menu.lst, to be automatically updated, but i use kde so that might be the issue.

---

### Post by MeURi on 2009-01-10
I use only Gnome, and I remember the menu.lst got updated automatically via synaptic.

I'll wait for the next kernel to see if my problems are solved.

---

### Post by dcstar on 2009-01-10
> **Green_Star said:**
> Hi,

My ubuntu 8.04, just installed with kernel 2.6.24-23 but it is not showing up in my boot menu. How do I enable it so that my ubuntu boots in to that kernal, I checked my menu.lst it is not there. Synaptic package showing as it is installed.

The last 8.04 kernel update presented my with a screen asking me if I wanted to keep my current menu.lst settings or use new ones - I selected "keep" and it did not enter this new kernel in the list (I did it manually later).

I believe that it should not have asked this question (my debconf is set to use Gnome so that is why I saw it) and installed the new kernel entry automatically, so it appears to be a bug in this particular package update. I suppose it should be reported, but I don't really know what category to put it in.

---

