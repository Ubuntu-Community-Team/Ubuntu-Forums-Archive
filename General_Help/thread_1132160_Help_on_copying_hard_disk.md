---
title: "Help on copying hard disk?"
date: 2009-04-21
forum: General Help
---

### Post by chris301up on 2009-04-21
I have just purchased another disk drive and now need to copy the entire contents of my existing drive onto the new one.

I have programmes for cloning hard disks using Windows operating systems, but they will not apparently work for Ubuntu 8.10.

Can anyone give me some advice regarding this?

---

### Post by Irony on 2009-04-21
This is the method I use;

[http://ubuntuforums.org/showthread.php?t=416710](http://ubuntuforums.org/showthread.php?t=416710)

You may have to alter your fstab file afterwards and you will have to perform grub install.

---

### Post by chris301up on 2009-04-21
> **Irony said:**
> This is the method I use;

[http://ubuntuforums.org/showthread.php?t=416710](http://ubuntuforums.org/showthread.php?t=416710)

You may have to alter your fstab file afterwards and you will have to perform grub install.

This all seems very complicated? Maybe it would be easier to just reinstall everything again from the beginning?

As you are probably aware I am quite new to this. What is a GRUB install?

---

### Post by Irony on 2009-04-21
Probably it would be easier to do a fresh install for you.

But for me I would do the above mentioned copying - then I would install grub to the MBR (hda) and point it to a menu.lst in hda3 do;

```
sudo grub
```

This opens up the grub program, with a prompt of

```
grub>
```

now type
 
```
find /boot/grub/stage1
```

then

```
root (hd0,2)
```

then

```
setup (hd0)
```

then

```
quit
```

I would then check your fstab file in the new drive - it takes about 10 minutes.

Grub is the program which does the booting up, for example you will see it if you have a dual boot with windows then it will pop up offering you the option of which distro to boot to.

On the other hand if you are merely adding the new drive to your computer so you have old and new drives then... probably it would still be easier for you do a fresh install.

---

