---
title: "Cann't install new kernel using apt-get - mkinitrd not working?"
date: 2005-01-14
forum: General Help
---

### Post by parktownprawn on 2005-01-14
For some reason I cann't install a new kernel using apt-get. The package won't configure after downloading. Trying to reconfigure the package doesn't help.

Typing:

$ sudo dpkg --configure linux-image-2.6.8.1-4-386

gives:

Setting up linux-image-2.6.8.1-4-386 (2.6.8.1-16.8 ) ...
/usr/sbin/mkinitrd: line 1095: cd: initrd: No such file or directory
Failed to create initrd image.
dpkg: error processing linux-image-2.6.8.1-4-386 (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.8.1-4-386

(also got similar output when i first ran apt-get install) 

I tried reinstalling initrd-tools but that didn't help.

the is a file /boot/initrd.img-2.6.8.1-4-386.new but  initrd.img-2.6.8.1-4-386
isn't there.  It seems that mkinitrd is broken but I have no idea why or how to fix it.

Any Ideas?

---

### Post by wallijonn on 2005-01-14
Why are you using --configure?

Why not just [COLOR=Red]apt-get -i linux-image-2.6.8.1-4-386[/COLOR] or install through SPM?

---

### Post by parktownprawn on 2005-01-14
Did you mean 

$ apt-get install linux-image-2.6.8.1-4-386 

since running apt-get -i gives:

$ sudo apt-get -i linux-image-2.6.8.1-4-386
Password:
E: Command line option ‘i’ [from -i] is not known.

Anyway I had initially installed the package using apt-get install but got similar output to the output of dpkg --configure

---

### Post by parktownprawn on 2005-01-17
I solved my own problem - stupid mistake on my part :

I had set $CDPATH  without including the current directory, "." which meant the script couldn't change to the current directory

---

