---
title: "Run BBC iPlayer Desktop 64bit Jaunty"
date: 2009-05-02
forum: General Help
---

### Post by Woody1987 on 2009-05-02
Im trying to get BBC iplayer to work on 64bit jaunty. I have managed to install adobe air using the 64bit instructions on the adobe website. I then downloaded and install the bbc iplayer app. Problem is, is that it wont run. If i run from the terminal i get:

> Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64


How do i solve this?

---

### Post by hyperdude111 on 2009-05-02
I too had problems with the 64 bit iplayer on ubuntu. The bbc was very unhelpful, after stating multiple times in an email that i was using linux NOT windows the sent me instructions about "activex and internet exporer, To top this off they then gave me a link to the microsoft website to help me troubleshoot my problem.

After a few days work i turned to get_iplayer, terminal only app but hassle free.

---

### Post by codeseer on 2009-05-02
> **Woody1987 said:**
> Im trying to get BBC iplayer to work on 64bit jaunty. I have managed to install adobe air using the 64bit instructions on the adobe website. I then downloaded and install the bbc iplayer app. Problem is, is that it wont run. If i run from the terminal i get:



How do i solve this?

Do you have that module installed? Do a listing for that directory and make sure the file is there.

---

### Post by Woody1987 on 2009-05-02
> Do you have that module installed? Do a listing for that directory and make sure the file is there.

matt@matt-desktop:~$ ls /usr/lib/gtk-2.0/modules/
libatk-bridge.so           libferret.so      libkeymouselistener.so
libcanberra-gtk-module.so  libgail-gnome.so
libdwellmouselistener.so   libgail.so

---

### Post by codeseer on 2009-05-02
> **Woody1987 said:**
> matt@matt-desktop:~$ ls /usr/lib/gtk-2.0/modules/
libatk-bridge.so           libferret.so      libkeymouselistener.so
libcanberra-gtk-module.so  libgail-gnome.so
libdwellmouselistener.so   libgail.so

Is ia32-libs up to date?

---

### Post by Woody1987 on 2009-05-02
> Is ia32-libs up to date?

indeed

---

### Post by codeseer on 2009-05-02
Found it: [https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/369498](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/369498)

Edit: The get_iplayer is 32-bit. You could try rolling the i32-libs back a version or two and see if that works.

---

### Post by hyperdude111 on 2009-05-04
> **codeseer said:**
> Found it: [https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/369498](https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/369498)

Edit: The get_iplayer is 32-bit. You could try rolling the i32-libs back a version or two and see if that works.

32 and 64

---

### Post by kitrule on 2009-05-08
Solution here -> [http://ubuntuforums.org/showpost.php?p=7237623&postcount=16](http://ubuntuforums.org/showpost.php?p=7237623&postcount=16)

---

### Post by timnic on 2009-05-11
Wow,

I have been looking everywhere for a solution and had just about given up every getting iplayer working on by 64 bit installation. Thanks to that simple link, It all works now! - Fantastic - Thanks so much :P

---

