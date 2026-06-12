---
title: "X doesnt start after reboot.."
date: 2005-03-12
forum: Desktop Environments
---

### Post by keffo on 2005-03-12
Hey hey
I have this problem who starts bugging me off.. 

This is pretty much my sys,
Ubuntu Hoary (latest) - 2.6.10-4-k7
fglrx-6-8-0_8.10.19-2_i386.deb

----

The problem is, when I rebooted meh computer this happens..
I get this little grayboxed error saying "I cannot start the Xserver
for you, would you like me to diagnose the problem" (almost like
that)


If I **rmmod fglrx ; dpkg -i --force-overwrite fglrx-6-8-0_8.10.19-2_i386.deb** 

And stop GDM and then start it, it works perfectly. I have about
4500 fps in glxgear and there is no problemos.

The problemo's just that I have to do this little thingie everytime
I boot my computer. And this really sucks, anyone got a clue?

*Best regards, thanks*

I paste links to Xorg.0.log.old AND Xorg.0.log

**[http://www.tehjunkyard.net/Xorg.0.log.old.txt](http://www.tehjunkyard.net/Xorg.0.log.old.txt)** 
**[http://www.tehjunkyard.net/Xorg.0.log.txt](http://www.tehjunkyard.net/Xorg.0.log.txt)**

---

### Post by keffo on 2005-03-12
This is what happens:

[size=1]```
root@keffo:/lib/modules/fglrx/build_mod # sh make.sh 
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.10-4-k7/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-4-k7'
  Building modules, stage 2.
  MODPOST
Warning: could not find /lib/modules/fglrx/build_mod/2.6.x/.libfglrx_ip.a.GCC3.cmd for /lib/modules/fglrx/build_mod/2.6.x/libfglrx_ip.a.GCC3
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-4-k7'
build succeeded with return value 0
duplicating results into driver repository...
done.
==============================
You must change your working directory to /lib/modules/fglrx
and then call ./make_install.sh in order to install the built module.
==============================
root@keffo:/lib/modules/fglrx/build_mod # cd ..           
root@keffo:/lib/modules/fglrx # sh make_install.sh      
- creating symlink
- recreating module dependency list
- trying a sample load of the kernel module
FATAL: Error inserting fglrx (/lib/modules/2.6.10-4-k7/kernel/drivers/video/fglrx.ko): Invalid module format
failed.
root@keffo:/lib/modules/fglrx # lsmod | grep gl
root@keffo:/lib/modules/fglrx # 
```[/size]

Any idea?

---

### Post by keffo on 2005-03-12
Ok, not even the 'script' wich copies those files etc work.. and its added to startup etc, hm.. i can see during the boot that its "loaded".
 

well, but no x or anythings booting up, but when i just run the script in console.. it
goes poff starting.


[edit]
my mate will paste it ;P

---

### Post by fackamato on 2005-03-12
[QUOTE=keffo]Ok, not even the 'script' wich copies those files etc work.. and its added to startup etc, hm.. i can see during the boot that its "loaded".
 

well, but no x or anythings booting up, but when i just run the script in console.. it
goes poff starting.


[edit]
my mate will paste it ;P PS. I r le gay[/QUOTE]

And here is the actual code:

[size=1]```
#!/bin/sh
case "$1" in
  start)
    echo " Unloading module fglrx..."
    modprobe -r -v fglrx
    echo " Done."
    echo " Copying /lib/modules/fglrx/build_mod/2.6.x/fglrx.ko to /lib/modules/2.6.10-4-k7/kernel/drivers/video/ ..."
    cp /lib/modules/fglrx/build_mod/2.6.x/fglrx.ko /lib/modules/2.6.10-4-k7/kernel/drivers/video/
    echo " Done."
    echo " Loading module fglrx..."
    modprobe -v fglrx
    echo " Done."
 ;;
  stop)
    echo " Yeah right. :P"
 ;;
 esac

```[/size]

---

