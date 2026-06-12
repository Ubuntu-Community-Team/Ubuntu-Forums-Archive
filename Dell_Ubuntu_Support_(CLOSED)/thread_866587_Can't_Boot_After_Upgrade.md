---
title: "Can't Boot After Upgrade"
date: 2008-07-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by clbaines on 2008-07-21
I have a Dell Inspiron E1505 Laptop. Single OS came that way and
will stay that way. I upgraded from 7.04 to 7.10 and I am having
problems getting it to boot. I have tried many of the solutions 
found here on the forum. I still cannot get it to boot. I know 
I am missing a trick somewhere.  Can there be something peculiar
only to these Dell factory preloads. What is the "dell utility"
on the first partition /dev/sda1?

As of now I go directly to grub when I turn the laptop on. If I
type Boot at the Grub> prompt I get a message to load the kernel
first. I did an fdisk -l so I know the correct boot partition
but  still get this error (Or I should say this is the error of
the day). Try something and it changes.

Would Dell have put grub in the MBR or in another partition?

I tried to ask Dell support but that was a waste of time.
Any thoughts?

---

### Post by Potatoj316 on 2008-07-22
Did you upgrade via a program or did you completly reinstall the OS?  Also did you try the Dell ubuntu help or the regular Dell help?

---

### Post by gbrainin on 2008-07-22
The "Dell utility" partition is a set of hardware testing utilities.  It's used by Dell to help diagnose problems.

It has not interfered with my upgrades from 7.04 -> 7.10 -> 8.04.

---

### Post by rogier.de.groot on 2008-07-22
If /dev/sda1 is the dell utility thing, which partition is the boot partition (or root partition if you don't use a seperate boot partition)?
The grub command line needs (working from memory so I might get things wrong - grub has help though) a "root" to work from, like:

root hd(0,0)

Where hd(0,0) means /dev/sda1, /dev/sda2 would be hd(0,1), /dev/sdb1 would be hd(1,0). Etc.

It then needs to know where the kernel and initrd are, like

kernel /boot/vmlinuz-VersionNumber KernelOptionsHere
initrd /boot/initrd-VersionNumber

Only then can you type "boot".

---

### Post by clbaines on 2008-07-22
I used the upgrade manager. I got a clean upgrade to 7.10. All things were
ok. I shut down and when I turned it on it would not boot.

---

### Post by falcon61102 on 2008-07-22
The update may not have reflected correctly in your GRUB menu.lst so the GRUB may be trying to access an old kernal that's not there anymore.

If you could post the menu.lst we may be able to see the problem.

Boot up with a LiveCD. 

Using your File Manager look around and on your primary partition you should see a folder called "boot" and in that one that says "grub".  Open that and inside you'll see a menu.lst.  Copy the contents of that here.

As a note, you can not edit your menu.lst unless your are the root user so if you have to edit it, go through the terminal using:
```
sudo gedit /(your mounted partition)/boot/grub/menu.lst 
```

---

### Post by clbaines on 2008-07-28
I don't have a menu.lst. What do you suggest. I have sarched on "grub m enu.lst". Looks like it could created but I don't know if it would help.

---

### Post by clbaines on 2008-07-28
> **rogier.de.groot said:**
> If /dev/sda1 is the dell utility thing, which partition is the boot partition (or root partition if you don't use a seperate boot partition)?
The grub command line needs (working from memory so I might get things wrong - grub has help though) a "root" to work from, like:

root hd(0,0)

Where hd(0,0) means /dev/sda1, /dev/sda2 would be hd(0,1), /dev/sdb1 would be hd(1,0). Etc.

It then needs to know where the kernel and initrd are, like

kernel /boot/vmlinuz-VersionNumber KernelOptionsHere
initrd /boot/initrd-VersionNumber

Only then can you type "boot".



I thought this would be it. I found the kernel and initrd but when  I try to boot from grub I `get a "file not found'.

I am fairly sure of my syntax for the commands. But when I search
with then vmlinuz command from the grub prompt I get a location
of (hd0,1) from find /vmlinuz.  Anything else to suggest?

---

### Post by clbaines on 2008-07-29
I can't find a menu.lst file. Looked in /boot/grub and did sudo find
and no luck. It seems to be missing. Any thoughts?

---

### Post by gbrainin on 2008-07-29
If you are 100% sure you don't have a menu.lst file (and you have tried everything I can think of to find it), then my guess is something got seriously honked up during your upgrade.  Personally, I would try a clean reinstall from a live CD, but that will lose all your data, so back up everything first.

---

### Post by falcon61102 on 2008-07-29
Well you can attempt to reinstall you GRUB.  Boot up and go to your terminal.  Make sure you mount your primary partition if it is not already mounted when you go through this. Run:
```
sudo grub
```
That will start the GRUB program and now allow you to edit/install your GRUB.  First you need to see if GRUB can locate itself or where it should be.  Type:
```
find /boot/grub/stage1
```

You should now get something like "hd(0,0)" back as a result of that command.  Whatever is printed when you run that command is what you need for the next command.

```
root hd(0,0)
```

That command tells the GRUB what partition is your root partition.  Now you want to setup the GRUB.  Basically, you need to take the "hd(0,0)" from the last command and use that, except this time you are only going to use the first number so if "hd(0,0)" is what you have been using, the you only use "hd(0)".  If you had been using "hd(1,0)" then you would use "hd(1)".

```
setup hd(0)
```

This last command is going to return approx 6-8 lines of code and will more than likely say succesful on the last line.  That is good, but if any of the lines end with "FAIL" then you may have a problem.  Most likely, you need to adjust the last step.  

If you don't get any lines ending in "FAIL" then GRUB was installed and you should be able to reboot and it work.  If you get errors at any stage, let us know.

---

### Post by clbaines on 2008-07-30
> **gbrainin said:**
> If you are 100% sure you don't have a menu.lst file (and you have tried everything I can think of to find it), then my guess is something got seriously honked up during your upgrade.  Personally, I would try a clean reinstall from a live CD, but that will lose all your data, so back up everything first.

I tried a Super Grub disk and still get the file not found error.
I had a thread that suggested I rebuild menu.lst. That seems a like
it would be a bit of work. I have an external WD Had Drive and will
back up /home and reinstall. I have 8.04 and could install it. I have 7.04 now. How would you partition and what file systems on what partitions?

---

### Post by gbrainin on 2008-07-30
> **clbaines said:**
> How would you partition and what file systems on what partitions?

Personally, I have a small primary /boot partition, a primary swap partition, and a large extended partition which is subdivided into a decent-sized / and a fairly large /home.  But partitioning is a matter of preference and how you plan to use it.

The nice thing about having a separate /home partition, of course, is that you simply don't format it when you upgrade, so you never lose the data.

---

