---
title: "Kernel update - grub annoyance"
date: 2006-08-03
forum: Desktop Environments
---

### Post by Brewtal on 2006-08-03
After an update to the kernel, grub will show multiple instances of ubuntu at the boot screen. How does one clean up grub?

Thanks.

---

### Post by cantormath on 2006-08-03
> **Brewtal said:**
> After an update to the kernel, grub will show multiple instances of ubuntu at the boot screen. How does one clean up grub?

Thanks.

Do you mean when you hit esc, you see several linux kernel installed?

---

### Post by Brewtal on 2006-08-03
No, when I first turn on my computer, after it detects hardware and goes into grub is where I see 2-3 instances of ubuntu to boot into, along with windows.

---

### Post by mlind on 2006-08-03
Remove your old kernels.

You can also disable unneeded menu options, like memtest and recovery mode. On /boot/grub/menu.lst find these options and set their value to false.

```

# memtest86=false
# alternative=false

```

---

### Post by Brewtal on 2006-08-03
> **mlind said:**
> Remove your old kernels.

You can also disable unneeded menu options, like memtest and recovery mode. On /boot/grub/menu.lst find these options and set their value to false.

```

# memtest86=false
# alternative=false

```

When you say remove old kernels are you refering to deleting from menu.lst, or actually uninstalling? This may sound stupid, but I don't want to foobar another installation.

---

### Post by mlind on 2006-08-03
> **Brewtal said:**
> When you say remove old kernels are you refering to deleting from menu.lst, or actually uninstalling? This may sound stupid, but I don't want to foobar another installation.

Actually uninstalling. You don't need to keep old kernel images lying around if your current kernel works fine.

---

### Post by webbie180 on 2006-08-03
How do I uninstall old images?

---

### Post by mlind on 2006-08-03
> **webbie180 said:**
> How do I uninstall old images?

```

sudo aptitude purge linux-image-**xxxx**

```

or use synaptic if you like graphical interface. 

When you type in that aptitude command, press <TAB> key before the xxxx part, so that you'll see list of installed kernel images and know what to remove.

---

### Post by cantormath on 2006-08-04
> **Brewtal said:**
>  grub is where I see 2-3 instances of ubuntu to boot into, along with windows.

what does it say?

---

