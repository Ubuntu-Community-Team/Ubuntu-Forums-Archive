---
title: "the name of Ubuntu is my problem -for expert"
date: 2009-03-18
forum: General Help
---

### Post by sudlex on 2009-03-18
Hy all;
am starting in customizing ubuntu 8.10 for making live cd  , it works well and fine " using reconstructer  " .
my problem that i canot change the name of ubuntu and live user session which appear when the system boot.
i have tried casper.conf but no things happen 
is there any thing more i can do ?

---

### Post by jflaker on 2009-03-18
bump?

---

### Post by sudlex on 2009-03-18
a big bump
i have tried with it for three days [IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG], finally i think may i found the solution here :popcorn:

---

### Post by fieroboom on 2009-03-18
I've never actually done what you're doing, but [googling a little,](http://www.google.com/search?hl=en&q=ubuntu+custom+livecd+change+username&btnG=Search) I found [this page](https://help.ubuntu.com/community/LiveCDCustomization#Boot%20init) indicating that you can change it, but it doesn't appear to be in casper.conf.

> Boot init

You have to edit the files in edit/usr/share/initramfs-tools/scripts/casper-bottom/* For example you can change the hostname or the livecd user.

i.e.

sudo nano edit/usr/share/initramfs-tools/scripts/casper

and edit the username or hostname

sudo nano edit/usr/share/initramfs-tools/scripts/casper-bottom/10adduser

to edit even the livecd user's password.

P.S. in order to obtain an encrypted password, you have to use the mkpasswd program that's shipped with whois package!

Rebuilding initrd

After you've modified the kernel, init scripts or added new kernel modules, you need to rebuild the initrd.gz file and substitute it into the casper directory."

Does that help?
:D
-Paul

---

### Post by sudlex on 2009-03-18
> **fieroboom said:**
> I've never actually done what you're doing, but [googling a little,](http://www.google.com/search?hl=en&q=ubuntu+custom+livecd+change+username&btnG=Search) I found [this page](https://help.ubuntu.com/community/LiveCDCustomization#Boot%20init) indicating that you can change it, but it doesn't appear to be in casper.conf.



Does that help?
:D
-Paul

thanks paul , i have tried it , again [COLOR="Red"]NO things change[/COLOR]

---

### Post by sudlex on 2009-03-18
[COLOR="Black"][CENTER]up   up[/CENTER][/COLOR]

---

### Post by sudlex on 2009-03-20
Am waiting ....

---

### Post by sudlex on 2009-03-21
thanks all , it have been solved using reconstructer and modify the file reconstructer/init/etc/casper.conf  "not in the root" and build it again :popcorn:

again thanks all and am ready for any qz ...

---

