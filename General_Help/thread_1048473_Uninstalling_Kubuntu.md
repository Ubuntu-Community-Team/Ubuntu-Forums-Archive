---
title: "Uninstalling Kubuntu"
date: 2009-01-23
forum: General Help
---

### Post by salijackt on 2009-01-23
I installed Kubuntu as a dual boot with my Windows Vista (gag!) laptop.  I wasn't real thrilled with kubuntu, so I installed Ubuntu.  Now I have Ubuntu, Vista, and Kubuntu all on my laptop (does that make it a triple boot?).  I no longer want Kubuntu, especially since I learned how to run KDE on Ubuntu.  How can I remove Kubuntu without removing Ubuntu or Windows?

---

### Post by gjoellee on 2009-01-23
Did you install Kubuntu and Ubuntu on the same partition? If so, you most likely installed ubuntu this way am I right?
```
sudo apt-get install ubuntu-desktop
```
If done so you are still just dualbooting, but if you installed Ubuntu on one partition and Kubuntu on one other that makes it a tripple boot.

If you have installed Ubuntu with "sude apt-get install ubuntu-desktop" just log into Ubuntu enter the temrinal and remove Kubuntu (Including all KDE applicaitions) with ```
sudo apt-get remove kde*
```

---

### Post by salijackt on 2009-01-23
They are on separate partitions...all three come up on GRUB.

Could you explain things thoroughly?  I don't understand the super technical stuff...

---

### Post by salijackt on 2009-01-28
Can anyone help me?

---

### Post by mb_webguy on 2009-01-28
You may be able to use GParted to delete the Kubuntu partition and expand your Ubuntu partition into the newly freed space, but it depends on how you have partitioned your drive.

My suggestion is to backup everything, especially your home directory and any files on your shared partition, if you're sharing one between Linux and Windows.  Use "fdisk -l" and your /etc/fstab file to identify your partitions, particularly the one for Ubuntu and the one for Kubuntu.  Then get either a Ubuntu or GParted LiveCD (since you can modify a partition while it's mounted), and open the partition editor.  Remove the Kubuntu partition, then try to expand whichever other partition you want into the unused space.

---

