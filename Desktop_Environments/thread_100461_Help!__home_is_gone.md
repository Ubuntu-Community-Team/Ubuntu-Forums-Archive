---
title: "Help!  /home is gone??"
date: 2005-12-07
forum: Desktop Environments
---

### Post by Vincent_Lin on 2005-12-07
After copyng a lot of files (~30GB, photos, home video, etc..)from USB HD over to newly installed Breezy at /home/vincent, /home became corrupted??

I will copy ls -l results as below:
p-wsr-s--t  15504 3710381765     1197505065     3788809269  2028-04-09 04:01 home

Ctrl-Alt-F1 log-in using my regular account (the one created duing lnstallation) prompts that "No directory, logging in with HOME=/".

gnome could not login with the message (sort of) "/home/vincent does not seem to exist. Do you want to use / instaed?  It might not work proprely if not using SafeMode. .... ..."

Is my file system corrupted?  Is there a way to bring it back?

I used all defalut options in terms of hd partition and file system types while installing Breezy, using shipit CD.  Ubuntu installation takes over the whole hd and installed itself fine.

IBM X31 with centrino 1.3, self-installed 80GB 2.5' hd.  ati radeon chip, etc...

Thanks for the help.

Vincent

---

### Post by soulestream on 2005-12-07
was /home on its own partition and how big was it. Is your drive actually full?


soule

---

### Post by Vincent_Lin on 2005-12-08
Thanks for replying.

/home is a directory of root.  My hd was partitioned by installer into 3 partitions:
/, /boot, and swap.  I hope it is not full yet, as df shows / still has around 13gb of space.

Do you think that's the sympton when a partition is full?

Vincent

---

### Post by Sokraates on 2005-12-08
First you have to see, if /home/vincent actually exists. Just use your favorite filemanager an browse a bit.

Then take a look into fstab

```
gedit /etc/fstab
```

If you see something like this

```
/dev/hda6       /home           ext3    defaults        0       2
```

your /home directory is mounted on a different partition, then /. If /home is not listed in fstab, it's on the same partition as /.

If you find this entry, and if /home/vincent exists, backup fstab

```
sudo cp /etc/fstab /etc/fstab.bak
```

and delete the entry mentioning /home. For this, you have to edit fstab as root:

```
sudo gedit /etc/fstab
```

After that, reboot.

Please tell us, what you have found.

---

### Post by syklitengutt on 2005-12-08
im no guru at this, but if you un terminal type su
and your password, then type nautilus
can you find the folder then....

If you have the folder root...
I lost some folders and found them this way.

---

### Post by Sokraates on 2005-12-08
[QUOTE=syklitengutt]im no guru at this, but if you un terminal type su
and your password, then type nautilus
can you find the folder then....

If you have the folder root...
I lost some folders and found them this way.[/QUOTE]

Not the best idea. You simply crate a root-console and then open nautilus as root. For searching files it suffices to remain a regular user.

Only if you need to edit system files and you know exactly, what you're doing, you should switch to root. On a sidenote: there's a "root-terminal" in gnome (dunno which menu, I use KDE) in case you need to issue a lot of commands as root.

---

### Post by Vincent_Lin on 2005-12-08
/etc/fstab does not have entry for /home.

root-terminal did not help me to see the folder.

I am really interested to see what might caused this, but I have no time to wait for the solution.  Sorry guys, I am going to re-install breezy now.  I had horay installed on this machine for more than 8 months.  Some minor issues but nothing this critical as file system corrupted.

Before I really going forward to re-installation, is there anything I should pay special attention to?  My machine is IBM x31, 512 MB ram, 80GB self-installed 5400rpm HD, ATI VGA chip, Centrino 1.3GHz notebook.  

Thanks to all.

Vincent

---

