---
title: "Ubuntu won't boot!!!"
date: 2009-06-22
forum: General Help
---

### Post by Xpire on 2009-06-22
Hi there,

Just this morning, Ubuntu's update manager popped up asking me to install updates. Didn't really look through the list, but after updating I noticed that grub's default was changed to memtest.

I also noticed that there were an extra 2 Ubuntu options. Now I've got Ubuntu 9.04, kernel 2.6.28-13-generic and recovery mode, and also Ubuntu 9.04, kernel 2.6.28-11-generic and recovery mode. So I'm assuming the update manager updated my kernel :mad:

Booting to any of these options doesn't work for some reason :( With normal mode, it just hangs at a blank screen.
When I bootup in recovery mode, it spits out a whole page of things, and gets up to.. 

[	0.005943] Checking 'hlt' instruction... OK.
[	0.023330] ACPI : Core revision 20080926
[	0.026552] ACPI: Checking initramfs for custom DSDT

and that's it! It just stays frozen at the end of this line...

Has anyone else had this problem after updating their kernel? :(

---

### Post by Xpire on 2009-06-23
Nothing? :( I really need to get into Ubuntu...

---

### Post by hangfire on 2009-06-23
First, see if there is an older kernel still listed in grub, and try to boot that.

Next, search for the word "root", see if it comes with different arguments. For example, **root (hd0,0)** is typical for a single purposed Linux workstation, while root **(hd0,2)** is common for dual boot Windows/Linux workstations. See if the most recent root line for your new kernel matches previous efforts. See if it makes sense for your partition scheme. Grub has a built-in command line editor during boot that allows you to change it and try a boot. At worst it won't work or will boot your other O/S.

-HF

---

### Post by coffeecat on 2009-06-23
> **Xpire said:**
> I also noticed that there were an extra 2 Ubuntu options. Now I've got Ubuntu 9.04, kernel 2.6.28-13-generic and recovery mode, and also Ubuntu 9.04, kernel 2.6.28-11-generic and recovery mode. So I'm assuming the update manager updated my kernel :mad:

The update manager didn't so much update your kernel as install a newer version, keeping the old one so that it can still be used if necessary. 2.6.28-11 is the old one and 2.6.28-13 is the newer one, and works quite fine on my system. It's normal to add two more entries for each new kernel so that you can boot up into the old kernel if anything goes wrong with the new one.

The fact that the grub menu is defaulting to memtest and that you can't boot up with the new kernel suggests that something went seriously wrong with the installation of the new kernel. The freeze at 'checking initramfs...' supports that conclusion. The initramfs for the new kernel is generated when the new kernel is installed.

Having said all that, have you tried selecting the 2.6.28.11 kernel line in the grub menu when you boot up? The old kernel will still be there and you should be able to boot up with it.

If you can boot up with the -11 kernel, post the contents of /boot/grub/menu.lst. At least then we can see what the installer ahs done to it. A reinstall of the -13 kernel might fix things, but let's have a look at menu.lst first.

---

### Post by terdon on 2009-06-23
I assume this is on a laptop right? Try rebooting and when you get to GRUB, select the new kernel and type

```

    acpi=off

```
then hit enter. That may let you install. If it does post back here and I'll help you set it as a default option in grub.

---

### Post by zeeeet on 2009-06-23
terdon, I was having a problem that was very similar and your solution worked for me. If you could help me make acpi=off a permanent addition to grub that would be great. thanks

---

### Post by Xpire on 2009-06-24
:O That's so strange...

At the time of my first post, version 11 and 13 both didn't work, I tried them at least 5 times each.

After reading the replies, I tried version 11 to get the details of menu.lst, and it worked! Feeling a bit hopeful, i tried version 13 and it also worked! It somehow auto-fixed itself... wonder what could have caused it? =\

Thanks for your help anyway guys! :) Sorry for wasting your time

---

### Post by terdon on 2009-06-24
Xpire: No worries, glad to hear you sorted it out.

zeeeet:  Sure, no problem. Its quite simple really, just edit the kernel line in your /boot/grub/menu.lst file: 

```
sudo gedit /boot/grub/menu.lst
```

Then scroll down past all the lines starting with "#", these are commented out. You should find an entry for your kernel that looks something like this:```


title       Ubuntu Linux, kernel 2.6.28-11-generic
root       (hd0,5)
kernel     /boot/vmlinuz-2.6.28-11-generic root=/dev/sda6 ro quiet splash 
initrd     /boot/initrd.img-2.6.28-11-generic
quiet

```

Just add "acpi=off" to the end of the kernel line, like so:
```

kernel        /boot/vmlinuz-2.6.28-11-generic root=/dev/sda6 ro quiet splash acpi=off

```

Then save the file and reboot.

---

