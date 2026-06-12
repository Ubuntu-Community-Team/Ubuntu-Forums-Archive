---
title: "linux headers"
date: 2006-10-03
forum: Desktop Environments
---

### Post by crowquill on 2006-10-03
im about at the end of manually installing the drivers for my ATI video card in this guide:

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.29.6_drivers_in_Ubuntu_Dapper_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.29.6_drivers_in_Ubuntu_Dapper_Manually)

im using method 2

i should also let you know im pretty inexperienced with linux.

anyways, when i run the command:
**sudo apt-get install linux-headers-2.6.12-26-386**


i get:[B]
E: Couldn't find package linux-headers-2.6.15-26-386[/B]

i ran uname -a and got:
**Linux greg-desktop 2.6.15-26-386 #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006 i686 GNU/Linux**

thanks in advance for any help!

---

### Post by GreenMarine on 2006-10-03
If you can't get the package from apt-get, I'd just grab the package directly from here: [http://packages.ubuntu.com/dapper/devel/linux-headers-2.6.15-23-386](http://packages.ubuntu.com/dapper/devel/linux-headers-2.6.15-23-386)

Which are the headers for i386 kernel 2.6.15. (Looks like you are typing 2.6.12, your instructions are probably older than the current kernel you are using?)

---

### Post by bulldog on 2006-10-03
. nvt

---

### Post by lamego on 2006-10-03
```
sudo apt-get-install linux-headers-$(uname -r)
```
If the headers can't be installed then you have a problem with your apt repositores, the kernel headers are included on the main repository.

---

### Post by crowquill on 2006-10-03
ok, using the command **sudo apt-get install linux-headers-2.6.15-23-386** i was able to successfully download and install.

now my problem is that when i run the command **sudo module-assistant build fglrx**

i get this error:

 Bad luck, the kernel headers for the target kernel version could   &#9618;
     &#9474; not be found                                                       &#9618;
     &#9474; and you did not specify other valid kernel headers to use.

&#9474; If the running kernel has been shipped with the Debian             &#9618;
     &#9474; distribution, please install the package                           &#9618;
     &#9474; linux-headers-2.6.15-26-386. If your kernel source tree (or        &#9618;
     &#9474; headers) is located in some non-usual location, please set the     &#9618;
     &#9474; KERNELDIRS environment variable to the path of this directory, or  &#9618;
     &#9474; (alternatively) specify the source directory we build for with     &#9618;
     &#9474; the --kernel-dir option in module-assistant calls.

---

### Post by crowquill on 2006-10-03
no ideas?

---

