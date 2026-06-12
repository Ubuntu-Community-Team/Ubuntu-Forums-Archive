---
title: "background pictures from XP HD"
date: 2009-02-08
forum: Desktop Environments
---

### Post by lucloubier on 2009-02-08
Hi!

I am using 8.04 on a dual boot XP machine with 2 HD (one for XP and one for 8.04).

I selected a picture on my XP pictures documents to become my background picture (I love it!). It shows up correctly after doing an action on the ntfs drive (otherwise it remains blank!).

Is there a way of having 8.04 to automatically mount the XP drive on boot ? 

I don't want to copy my picture onto the Ubuntu partition...

I'm sure someone knows how to do it !

---

### Post by cyfur01 on 2009-02-08
Only way I know to do this is to edit your /etc/fstab folder. Do take note that messing up this file could prevent your primary partition from mounting when Ubuntu launches.

Press Alt+F2 and then type "gnome-terminal" to launch a terminal. Then:
```

sudo cp /etc/fstab /etc/fstab.bak
sudo gedit /etc/fstab

```
This will backup your fstab file (incase you mess it up), and then open the active copy for editing in gedit.

Next, add a line like this:
```

/dev/sda2   /xp     ntfs    default 0       0

```
to the **end** of the fstab file, **except note that you will probably have to change /dev/sda2 to a different device**. If you're not sure which device your XP partition is, I would recommend installing gparted (from Synaptic), and then running it from System->Administration->Partition Editor. From here, figure out which partition is your XP partition, and the device name will be under the "Partition" heading.
Also, if you would like to mount the partition to somewhere other than /xp, then change that portion of the entry as well. Once you're done, save the file and close gedit.

From the terminal window, type "sudo mount -a" and this will attempt to remount everything according to your edited fstab file. If there are any errors, run "cp /etc/fstab.bak /etc/fstab" to restore your backed-up fstab file, and you can give it another try.

Finally, reapply the background you want, going through /xp (or whatever you called it) and it should work from now on.

Edit:
As an alternative, you can install disk-manager (from synaptic), and this will then be found under System->Administration->Disk Manager. Then, under Advanced Configuration, you can set where you wish for your partitions to be mounted.

---

### Post by Yashiro on 2009-02-10
Just copy the picture to your Linux home folder. You're going to too much trouble just to display a picture.

---

