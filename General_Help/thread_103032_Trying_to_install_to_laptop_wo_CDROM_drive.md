---
title: "Trying to install to laptop w/o CDROM drive"
date: 2005-12-13
forum: General Help
---

### Post by tofu1 on 2005-12-13
I have a card reader and 1gb cf card. Is there a way to download the ISO onto the CF card and install it from there? I know it'll take forever but I don't want to go buy an external CD drive and plug it in..

---

### Post by kaamos on 2005-12-13
Does the laptop have any OS installed and do you have an Internet connection?

It might be easier to do a netinstall.. An installed OS is not required for that, but it makes life easier. At least for me it did. :)

---

### Post by tofu1 on 2005-12-13
I currently have XP on it. I want to wipe off every trace of that =)

Any step by step directions? Please and thanks!

---

### Post by Ocxic on 2005-12-13
Maybe this might help?
[http://ubuntuforums.org/showthread.php?t=28948](http://ubuntuforums.org/showthread.php?t=28948)

---

### Post by kaamos on 2005-12-14
Try the directions that Ocxic linked to. Note that these are for Ubuntu 5.04, and you probably want to install 5.10 so in the directions change this:
> #2 ~ Setting up the kernel

We only need to download two files for the installer to work...

linux.bin
initrd.gz

both of these we could download from the ubuntu archive.
place both of these files in C:\boot
- you'll probably have to create this directory yourself

to this:
> 2 ~ Setting up the kernel

We only need to download two files for the installer to work...

linux.bin
initrd.gz

both of these are here: [http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/images/netboot/ubuntu-installer/i386/](http://archive.ubuntu.com/ubuntu/dists/breezy/main/installer-i386/current/images/netboot/ubuntu-installer/i386/)
place both of these files in C:\boot
- you'll probably have to create this directory yourself

If you have any problems, post them here so we can try to help. :)

---

