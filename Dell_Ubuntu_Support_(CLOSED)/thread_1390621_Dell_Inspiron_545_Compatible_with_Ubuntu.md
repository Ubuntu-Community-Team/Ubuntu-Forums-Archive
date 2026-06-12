---
title: "Dell Inspiron 545: Compatible with Ubuntu?"
date: 2010-01-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by euclidnet on 2010-01-25
I am planning to get a Dell Inspiron 545 soon. Does anyone know if this
is compatible with Ubuntu?

---

### Post by efflandt on 2010-01-26
Do you mean 1545?  Yes it works great.  Just shrink the Win7 partition from Admin tools of Win7 itself and use gparted from the Ubuntu live/install CD to set up whatever partitions you want for Linux (I always prefer to set them myself than rely on auto partitioning by installation).

Once installed, the only special thing you need to do is activate **Broadcom STA** from System > Administration > Hardware Drivers for wireless, or if you do not have temporary ethernet connection, add (check) the installation CD as a source for Synaptic and install bcmwl-kernel-source package.  Everything else works out of the box.

Note that the function keys are the opposite of normal.  In other words the F2 key toggles wireless on/off and Fn+F2 inputs the F2 key.  So if wireless fails to work after installing or activating Broadcom STA, try hitting that key just in case you accidentally turned it off (a friend accidentally did that and got all excited because her wireless stopped working).

---

### Post by euclidnet on 2010-01-26
Hi [efflandt]("http://ubuntuforums.org/member.php?u=937632"),

Thank you for your reply. But really did mean "Inspiron 545" and not the "Inspiron 1545".

"Inspiron 545" is a desktop and this is what I am planning to get.

---

