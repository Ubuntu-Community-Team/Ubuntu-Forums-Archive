---
title: "Automatically set new custom kernel as default"
date: 2006-06-30
forum: Desktop Environments
---

### Post by Jeigh on 2006-06-30
I recently have been tasked with creating a custom kernel for a set of system we are running here and got through the process easily enough. My only issue currently is that upon installing the new kernel I want it to become the default kernel that is booted in grub. I know I can go into the grub configuration file and switch the default menu option, but I was wondering if there is a way to do this automatically? I know when you upgrade to a newer kernel using apt-get it becomes the default and assume there is a similar way to do this with a custom kernel.

The main reason I was hoping to do this is because we will be putting this onto alot of systems and I really don't feel like editing the menu.lst on each one. Thanks in advance for any suggestions.

---

### Post by knn on 2006-06-30
[QUOTE=Jeigh]I recently have been tasked with creating a custom kernel for a set of system we are running here and got through the process easily enough. My only issue currently is that upon installing the new kernel I want it to become the default kernel that is booted in grub. I know I can go into the grub configuration file and switch the default menu option, but I was wondering if there is a way to do this automatically? I know when you upgrade to a newer kernel using apt-get it becomes the default and assume there is a similar way to do this with a custom kernel.

The main reason I was hoping to do this is because we will be putting this onto alot of systems and I really don't feel like editing the menu.lst on each one. Thanks in advance for any suggestions.[/QUOTE]

Installing custom kernels (built using make-kpkg and installed using dpkg) always made them default for me. Maybe it's because the version number was always higher than the current (Ubuntu) kernel.

---

### Post by ayoli on 2006-06-30
another way is to make a pretty preinst script.
have a look in a kernel-image*.deb with file-roller find preinst in control.tar.gz, but it seems a bit complicated :)

---

### Post by Jeigh on 2006-07-04
Yea I'm pretty sure getting involved with scripts will be more work then I have the time to put into this heh, and I didn't intend to use a version of the linux kernel that would stick it at the top just by the default ordering methods so... anyone know of any other ways to do this maybe? lol

---

### Post by Thund3rstruck on 2006-07-04
You'll want to backup your mbr first (substitute hda with your / partition)
```

sudo dd if=/dev/hda of=/root/hda.mbr bs=512 count=1

```

then backup your grub bootloader configuration
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup

```
Now edit the bootloader list to meet your needs
```

sudo vi /boot/grub/menu.lst

```

or in a gui
```

sudo gedit /boot/grub/menu.lst

```

---

### Post by Jeigh on 2006-07-04
Yea I know how to go about changing the default kernel to boot. What I want to do is have it so that the compiled kernel sets the new kernel as the default to boot. Basically I want to be able to take the final .deb file, install it on new machines, reboot and have it boot into this kernel rather then needing to edit each individual menu.lst

---

