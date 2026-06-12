---
title: "How to install KeePass???"
date: 2006-02-12
forum: Desktop Environments
---

### Post by josh34 on 2006-02-12
I have KeePass (password manager) installed on my Windows machine and I love it. I resently installed Ubuntu on an old computer and now I want access to my passwords on my Ubuntu machine. I have tried installing KeePass the way described on their website, but I get errors and the installation aborts. My question is, how do I install KeePass on Ubuntu 5.10 with kernel version 2.6.12-10-386? KeePass website: [http://keepass.berlios.de/index.php?lang=english](http://keepass.berlios.de/index.php?lang=english)

Thanks,
Josh

---

### Post by kaamos on 2006-02-12
Hello!

You should download this package to your desktop: [http://home.arcor.de/tareks/keepass-0.1.3/keepass_0.1.3_i386.deb](http://home.arcor.de/tareks/keepass-0.1.3/keepass_0.1.3_i386.deb)
And then open a terminal (Applications -> Accessories -> Terminal) and
```
cd Desktop
sudo dpkg -i keepass_0.1.3_i386.deb
```

Hope this helps!

---

### Post by josh34 on 2006-02-12
I did that and I got this:
josh@ubuntu:~$ cd Desktop
josh@ubuntu:~/Desktop$ sudo dpkg -i keepass_0.1.3_i386.deb
Selecting previously deselected package keepass.
(Reading database ... 61912 files and directories currently installed.)
Unpacking keepass (from keepass_0.1.3_i386.deb) ...
Setting up keepass (0.1.3-1) ...
josh@ubuntu:~/Desktop$

But now how do I start KeePass?

Thanks,
Josh

---

### Post by kaamos on 2006-02-12
if it does not appear the menu you can open it in a terminal by typing "keepass". If it works ok, you can use the menu editor to add an entry to the menu.

---

### Post by josh34 on 2006-02-12
I typed keepass into terminal and I got this:
josh@ubuntu:~$ keepass
keepass: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory
josh@ubuntu:~$

What do I do now?

Thanks,
Josh

---

### Post by kaamos on 2006-02-12
Try again after this:
```
sudo apt-get install libqt3-mt
```

---

### Post by josh34 on 2006-02-12
That did the trick!

Thanks,
Josh

---

