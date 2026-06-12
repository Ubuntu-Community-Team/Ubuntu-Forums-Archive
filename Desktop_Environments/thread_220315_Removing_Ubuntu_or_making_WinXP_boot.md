---
title: "Removing Ubuntu or making WinXP boot"
date: 2006-07-21
forum: Desktop Environments
---

### Post by TacticalSniper on 2006-07-21
Hey, all.

I've tried looking for this in the forums and other support resources.
I want to know how do you uninstall Ubuntu or set my previously installed WindozeXP partition as bootable by default in LILO?

Thanks in advance. :cool:

---

### Post by PaulMellors on 2006-07-21
if you want to reinstall windows xp, you have to run the recovery console and fixboot and then fixmbr to remove grub and restore the master boot record then install XP, not sure about the lilo option

---

### Post by TacticalSniper on 2006-07-21
Well, I have no need to re-install Windoze. When the computer starts the LILO starts. Now you can change the commands there for every line, and I guess command "boot" says which of the kernels and other OS will be booted by default. However, I couldn't understand how to save commands you edited.

---

### Post by reclusivemonkey on 2006-07-21
> **TacticalSniper said:**
> Well, I have no need to re-install Windoze. When the computer starts the LILO starts. Now you can change the commands there for every line, and I guess command "boot" says which of the kernels and other OS will be booted by default. However, I couldn't understand how to save commands you edited.

After making any changes to /etc/lilo.conf you have to run

```

lilo

```

every time. If you have made any mistakes, lilo should inform you of this.

---

### Post by TacticalSniper on 2006-07-21
So I should put "boot" under Windows and delete same thing from Ubuntu? Thus making Windoze default system? Okay, I think I get it.

Now, how do I uninstall Ubuntu, if there's a way.

---

### Post by cptnapalm on 2006-07-21
well, its an operating system so formatting the drive would be your best bet.

---

### Post by reclusivemonkey on 2006-07-22
> **TacticalSniper said:**
> So I should put "boot" under Windows and delete same thing from Ubuntu? Thus making Windoze default system? Okay, I think I get it.

Now, how do I uninstall Ubuntu, if there's a way.

Post the entire contents of /etc/lilo.conf so I can have a look at what you have. You can't simply uninstall Ubuntu and it will magically boot back into Windows; you need to reinstall the mbr for Windows. To do this you need the Windows fdisk utility and will need to do

```

C:\ fdisk /mbr

```

---

### Post by TacticalSniper on 2006-07-22
Well, I won't even need the FDisk, cause the recovery console can do same thing with fix mbr I think, and you can run it from inside Windoze.

Oh, I don't expect any "magic" :)

I'll post the content of the file in a bit. The thing is if I fix the MBR through console I won't know how to access Ubuntu after that.

---

