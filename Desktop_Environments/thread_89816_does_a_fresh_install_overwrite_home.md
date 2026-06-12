---
title: "does a fresh install overwrite /home/*** ?"
date: 2005-11-13
forum: Desktop Environments
---

### Post by kamaaina on 2005-11-13
I read that the solution to my segmentation fault on synaptic was to do a fresh install from the CD.  My wife's laptop was recently updated to 5.10 by placing the CD in the drive updating from Synaptic.  Now, running 5.10 she has segmentation faults when starting Synaptic.  So, I would like to do a fresh install if that solves the problem but I don't want her to loose all her personal settings, evolution mail, contacts, etc.  

Can anyone explain what happens when I do a fresh install from the CD with regards to the user data?

Thanks

---

### Post by aysiu on 2005-11-13
Do you have a separate /home partition? Or is it just a /home folder?

---

### Post by kamaaina on 2005-11-13
its just a /home folder on the partition as everything else.

---

### Post by ace2005 on 2005-11-13
My Synaptic also seg faults but its ok when i run sudo synaptic, i just reinstalled since i messed up juk while installing KDE 3.5.

Also try installing gnome-sudo

---

### Post by dbott67 on 2005-11-13
[QUOTE=kamaaina]its just a /home folder on the partition as everything else.[/QUOTE]
When you do a fresh install, you will re-partition the drive, which will destroy everything on the current partition (including your wife's home directory).

If you have a USB drive (or CD burner, etc.) you could copy everything from her home directory onto it.

During the new installation, you could create another partition just for data and then mount the /home directory to it.  Any future re-installations would not require you to worry about losing data in the /home directories.

-Dave

---

### Post by Qrk on 2005-11-13
If you do install again, your /home will be gone. But you can use the partitioner part of the installer or the Live CD to resize your ubuntu partition and make another ext3 partition on the new free space. Then copy your home directory to that partition and proceed to reinstall Ubuntu.

---

### Post by kamaaina on 2005-11-13
Well Dave I'll give that a try if nothing else works.  Thanks for the input everyone.  
gnome-sudo was not installed.  This surprised me, since I know that Ubuntu uses &#12288;sudo alot.  After doing apt-get install gnome-sudo I got this:

```

aya@ayalaptop:~$ sudo synaptic

Password:

Segmentation fault

aya@ayalaptop:~$

```

Any more thoughs?  Again thanks for all the pointers.

---

### Post by kamaaina on 2005-11-13
I'm a bit reluctant to split up the drives because that puts a hard limit on the size of my /home or / partitions.  I had that on an old computer with a admittedly smaller HD (12Gb) and I filled up one of the partitions quickly and had tons of empty space on the other partition.

---

### Post by dbott67 on 2005-11-13
You could split the drive into 2 (relatively) small partitions (1 for Ubuntu & 1 for /home) but leave a big chunk unallocated.  As your system requires more space for either partition, you can use gparted to 'grow' each partition as required.

In fact, this what one of our software vendors does on our AIX system.  Half of the hard drive space is unallocated after installation. Then, as required, the vendor can increase the size of various partitions as needed.

-Dave

---

### Post by kamaaina on 2005-11-13
Hmm I like that idea. &#12288;A bit complicated but at least it gives us the options.  So your saying just leave the space unallocated?  i.e., not partitioned as any kind of file system?

Thanks

---

### Post by kamaaina on 2005-11-13
Well I guess nothing is simple!

```
noah@noahlaptop:~$ gparted

(gparted:20232): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Fontconfig error: "local.conf", line 20: no element found
noah@noahlaptop:~$ sudo gparted

(gparted:20234): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Fontconfig error: "local.conf", line 20: no element found

glibmm-ERROR **:
unhandled exception (type std::exception) in signal handler:
what: locale::facet::_S_create_c_locale name not valid

aborting...
Aborted
noah@noahlaptop:~$
```

---

### Post by kamaaina on 2005-11-13
But on a more positive note: 
Thanks for all the help and I think I will try the gparted solution when I get it back up and running.

---

