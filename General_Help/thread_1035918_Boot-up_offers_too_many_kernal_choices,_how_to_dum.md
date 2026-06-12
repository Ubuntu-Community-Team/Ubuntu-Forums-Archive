---
title: "Boot-up offers too many kernal choices, how to dump some?"
date: 2009-01-10
forum: General Help
---

### Post by Ian Drummond on 2009-01-10
This has probably been asked many times before but, when I boot up I am offered about 12 different kernel choices to boot into. Is there a way to get rid of the old kernels which presumably are still in residence on the hard drive?

Sincerely,


Ian.

---

### Post by chriskin on 2009-01-10
if what you need is not to see all of those choices, you can use
gksudo gedit /boot/grub/menu.lst and delete those you do not want

---

### Post by oldos2er on 2009-01-10
Use Synaptic Package Manager to uninstall kernels you no longer want; doing so will automatically update your menu.lst.

---

### Post by glotz on 2009-01-10
[QUOTE=oldos2er]Use Synaptic Package Manager to uninstall kernels you no longer want; doing so will automatically update your menu.lst.[/QUOTE]
This is the post you should really be thanking. Also, by doing that you'll reclaim something like a gig of disk space. It might be a good idea to leave the newest and the second newest kernel in case you have a problem with the latest.

Kernels really aren't handled automatically, only new ones are piled in, it's pretty silly still. I'm optimistic surely we'll see improvements soon though.

---

### Post by bryncoles on 2009-01-10
also, you could install start-up manager from synaptic, as that will allow you to configure quite a bit about the grub-menu, including the number of kernels shown. i limit mine to two, in case i ever need to boot from an old kernel!

---

### Post by rahul_bhise on 2009-01-22
i went to synaptic manager and to remove the 2.6.24-19 kernel i "completely" removed the below 
```
linux-headers-2.6.24-19
linux-headers-2.6.24-19-generic
linux-image-2.6.24-19-generic
linux-restricted-modules-2.6.24-19-generic
linux-ubuntu-modules-2.6.24-19-generic
```
did i do it right

---

### Post by glotz on 2009-01-22
Oh yeah.

Bonus remove: If you're not going to compile any extra modules for your current kernel, I'm under the impression you can also ditch the header files for the kernel you're now on. (And ditto for any other kernels.)

---

### Post by mgol on 2009-01-22
Edit Your /boot/grub/menu.lts file. Search for the lines:
```

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

```
and change the last line to:
```
# howmany=2
```
as it's good to have at least one additional kernel, in case of a failure (even though it shouldn't happen).
Then (but only if You didn't edit the entries manually, because it will overwrite everything You entered in the "Debian automagic" section) invoke:
```
sudo update-grub
```

menu.lst file is very well commented, just read those comments - as You see, everything is explained here.

---

### Post by Yashiro on 2009-01-22
> Use Synaptic Package Manager to uninstall kernels you no longer want; doing so will automatically update your menu.lst.

Make VERY sure you're removing the right versions. Search for *linux-image* in Synaptic.

---

