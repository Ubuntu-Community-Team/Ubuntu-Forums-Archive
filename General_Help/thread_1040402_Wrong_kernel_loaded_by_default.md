---
title: "Wrong kernel loaded by default?"
date: 2009-01-15
forum: General Help
---

### Post by fastpakr on 2009-01-15
I apologize in advance if I fail to provide adequate information or sound like a newbie at some point...

My parents have a Dell that was purchased with an OEM 8.04 32 bit install.  Since that time, I've run an in-place upgrade to 8.10.  I noticed today while trying to install VirtualBox on the pc that the active linux kernel was 2.6.24-16.  I verified the installed kernels with 'dpkg --list | grep linux-image' and got:
> ii  linux-image-2.6.24-16-generic              2.6.24-16.30                            Linux kernel image for version 2.6.24 on x86
ii  linux-image-2.6.24-19-generic              2.6.24-19.41                            Linux kernel image for version 2.6.24 on x86
ii  linux-image-2.6.24-21-generic              2.6.24-21.43                            Linux kernel image for version 2.6.24 on x86
ii  linux-image-2.6.24-22-generic              2.6.24-22.45                            Linux kernel image for version 2.6.24 on x86
ii  linux-image-2.6.27-9-generic               2.6.27-9.19                             Linux kernel image for version 2.6.27 on x86
ii  linux-image-generic                        2.6.27.9.13                             Generic Linux kernel image

I checked /boot/grub/menu.lst and it appears that the only kernels listed as boot options are:
> title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=4f6268af-8e68-4aa4-8875-75dc99cb9d68 ro all_generic_ide quiet splash
initrd          /boot/initrd.img-2.6.24-16-generic
quiet

title           Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=4f6268af-8e68-4aa4-8875-75dc99cb9d68 ro all_generic_ide quiet
initrd          /boot/initrd.img-2.6.24-16-generic

title           Ubuntu 8.04, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

The machine is definitely running 8.10.  Is there something obvious that I'm missing as to why GRUB is configured to load the wrong kernel and indicates the wrong Ubuntu release?  Any help would be greatly appreciated.

---

### Post by Titan8990 on 2009-01-15
Look at the top of the menu.lst file:

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

```

The value of default is what defines which kernel it will boot by default.

---

### Post by _sleeper on 2009-01-15
apparently the menu.lst hasn't been updated, but you can do it manually.

```

gksu nano /boot/grub/menu.lst

```

and edit the lines.

---

### Post by fastpakr on 2009-01-15
> **Titan8990 said:**
> Look at the top of the menu.lst file:

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

```

The value of default is what defines which kernel it will boot by default.

I understand that the default value refers to which option below to use, but NONE of the options below reference the current kernel.  So how is the default value option really relevant?

---

### Post by drs305 on 2009-01-15
there is a nice gui-based app called StartUp-Manager that can set the grub menu.lst items without manually editing menu.lst. It can select the default kernel or OS, how many kernels to display in the menu, menu timeout, and a lot more.

Check the link in my signature for a tutorial on how to install and run StartUp-Manager (SUM). What you want is in section 1.

---

### Post by fastpakr on 2009-01-15
> **_sleeper said:**
> apparently the menu.lst hasn't been updated, but you can do it manually.

```

gksu nano /boot/grub/menu.lst

```

and edit the lines.

Thanks.  I understand how to edit it, but wanted to find out why it might not have been updated before hacking away at it.  Any ideas as to why it's still stuck on an ancient kernel?

Also, just to be sure - if I edit the first section to the following I'm all set, right?
> title           Ubuntu 8.10, kernel 2.6.27-9-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.27-9-generic root=UUID=4f6268af-8e68-4aa4-8875-75dc99cb9d68 ro all_generic_ide quiet splash
initrd          /boot/initrd.img-2.6.27-9-generic
quiet

---

### Post by sisco311 on 2009-01-15
try to generate a new menu.lst file.

back up the old:
```
sudo mv /boot/grub/menu.lst /boot/grub/menu.lst-backup
```

then:
```
sudo update-grub
```

or you can add manually the new kernel entries:
> title Ubuntu 8.10, kernel 2.6.**27-19**-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.**27-9**-generic root=UUID=4f6268af-8e68-4aa4-8875-75dc99cb9d68 ro all_generic_ide quiet splash
initrd /boot/initrd.img-2.6.**27-9**-generic
quiet

---

### Post by Titan8990 on 2009-01-15
Yes, should work fine. The only reason I can think is that your boot partition is separate from your rootfs. It is common to set /etc/fstab for your boot partition to NOT automount. So whenever the update went to upgrade menu.lst, it was not there due to the drive not being mounted.


Just a theory. 


And that kernel is FAR from "ancient." I would only consider it ancient if it was a 2.4.

---

### Post by _sleeper on 2009-01-15
> **fastpakr said:**
> Thanks.  I understand how to edit it, but wanted to find out why it might not have been updated before hacking away at it.  Any ideas as to why it's still stuck on an ancient kernel?

Also, just to be sure - if I edit the first section to the following I'm all set, right?

yeap, that's it!

---

### Post by fastpakr on 2009-01-15
Thanks to everyone for the rapid responses.

When I ran 'sudo update-grub' I got:
> Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... found: /boot/grub/splash.xpm.gz
Found kernel: /boot/vmlinuz-2.6.27-9-generic
Found kernel: /boot/vmlinuz-2.6.24-22-generic
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

When I checked menu.lst afterwards, it was unchanged.  Weird that it sees the newer kernel but doesn't make any adjustments to use it.  Any ideas?

---

### Post by Titan8990 on 2009-01-15
Try temporarily moving your menu.lst to see it forces to generate a new one:


sudo mv /boot/grub/menu.lst /boot/grub/menu.lst.bak

sudo update-grub


Now check your menu.lst. If needed:


cp /boot/grub/menu.lst.bak /boot/grub/menu.lst


No sense in throwing out the backup.


Someone yesterday also encountered this issue for unknown reason. It might be time to bug report it.

---

### Post by drs305 on 2009-01-15
> **fastpakr said:**
> When I checked menu.lst afterwards, it was unchanged.  Weird that it sees the newer kernel but doesn't make any adjustments to use it.  Any ideas?

There is a section in menu.list:
```

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

```

Make sure this setting to 'true'.

In StartUp-Manager, Advanced tab, tick "Automatically update default boot option"

Added referencing next post: The reason it worked when you moved the original menu.lst was even if this setting was set to 'false' there was no entry to update.

---

### Post by fastpakr on 2009-01-15
> **Titan8990 said:**
> Try temporarily moving your menu.lst to see it forces to generate a new one:


sudo mv /boot/grub/menu.lst /boot/grub/menu.lst.bak

sudo update-grub


Now check your menu.lst. If needed:


cp /boot/grub/menu.lst.bak /boot/grub/menu.lst


No sense in throwing out the backup.


Someone yesterday also encountered this issue for unknown reason. It might be time to bug report it.
Good call - removing the menu.lst before running update-grub did create a correct file.  Wish I understood why it wasn't editing it before.  Thanks for all the help!

---

### Post by fastpakr on 2009-01-15
> **drs305 said:**
> There is a section in menu.list:
```

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

```

Make sure this setting to 'true'.

In StartUp-Manager, Advanced tab, tick "Automatically update default boot option"

OK, I went back and put in the original menu.lst, changed updatedefaultentry to true, and re-ran update-grub.  That time it flagged the differences and made the changes.  What is the normal setting for that field?  My own desktop is also set to false, but it's a clean slate 8.10 install so it hasn't had any kernel updates just yet.

---

### Post by Titan8990 on 2009-01-15
Just checked mine. By default, in 7.10 it was commented out. I assume that if there isn't a updatedefaultentry=false it assumes true.

---

### Post by jocko on 2009-01-15
man update-grub says:
>        # updatedefault=true
       # updatedefault=false

       This option controls if grub should update the default  entry  to  keep
       booting the same kernel even if a new one is installed.

So, when set to "false", the new kernel will become the first option, which is the normal behaviour. If you by some reason want to keep using an older kernel even if there is a newer one, you may want to change it to "true".
At least that's my interpretation of the text...
And (from /boot/grub/menu.lst):
> ### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## [COLOR=Red]DO NOT UNCOMMENT THEM, Just edit them to your needs[/COLOR]
So, don't uncomment lines in menu.lst. update-grub will look for it's settings in lines starting with a single "#", so uncommenting lines would probably give the same result as deleting them completely...

---

### Post by drs305 on 2009-01-15
> **Titan8990 said:**
> Just checked mine. By default, in 7.10 it was commented out. I assume that if there isn't a updatedefaultentry=false it assumes true.

The comments in menu.lst are a bit different that in most files. If you look at the file there is a section called "Begin Automagic Kernels List" and ends just before the first menu item you actually see.

This section is defined by a single # all the way down and a single-commented line is acted upon, i.e. it is **not** treated as a comment. Double #'s are comments in this section. Think of it this way: single # = no comment, double # = comment.

So the line:
```

# updatedefaultentry=false

```
is acted upon. (well, actually it is read and not acted upon since the value is 'false')

Note you do not remove any comment symbols in this section. You should only change the values of the entry after the = symbol for most entries.

---

