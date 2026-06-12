---
title: "build hoary ati driver"
date: 2005-03-13
forum: Gaming &amp; Leisure
---

### Post by caracho on 2005-03-13
Hi,

I'm trying to build the new ati driver module for Hoary (xorg), I get this message :

```

root@ubuntu:/lib/modules/fglrx/build_mod # sh make.sh
ATI module generator V 2.0
==========================
initializing...
kernel includes at /usr/src/linux/include not found or incomplete
file: /usr/src/linux/include/linux/version.h
root@ubuntu:/lib/modules/fglrx/build_mod #


```

I've downloaded the kernel sources, but it seems that the file version.h does not exist in this version

Thanks for help

cara

---

### Post by caracho on 2005-03-13
Ok 

For those intersted, you must also install the kernel headers 

 :smile:

---

### Post by caracho on 2005-03-13
Now I can build the driver but I can't modprobe it

```

root@ubuntu:/home/alex # modprobe fglrx
FATAL: Error inserting fglrx (/lib/modules/2.6.10-4-386/misc/fglrx.ko): Invalid module format
root@ubuntu:/home/alex #

```

Any idea ?

---

### Post by bobmitch on 2005-03-13
[QUOTE=caracho]Now I can build the driver but I can't modprobe it

```

root@ubuntu:/home/alex # modprobe fglrx
FATAL: Error inserting fglrx (/lib/modules/2.6.10-4-386/misc/fglrx.ko): Invalid module format
root@ubuntu:/home/alex #

```

Any idea ?[/QUOTE]


Did you copy your fglrx.ko generated file from /lib/modules/fglrx/ to /lib/modules/*kernelversionhere*/misc/

?

---

### Post by caracho on 2005-03-13
yes

---

### Post by bobmitch on 2005-03-13
Did you **rmmod fglrx** before you started, as well as delete/move any existing fglrx.ko files?

I know these are basic questions, but I`ve made the same mistakes too many times. :)

---

### Post by caracho on 2005-03-13
yes yes : I am lost

---

### Post by bobmitch on 2005-03-13
[QUOTE=caracho]yes yes : I am lost[/QUOTE]

Me too I`m afraid.

---

### Post by CannoNFd on 2005-03-13
if make_install.sh gave an error then you need to do the following:

Modprobe works if you do make with gcc 2.96

To compile using gcc 2.96 open the make.sh file and remove the # from this line: #CC=gcc -V 2.96

After sh make.sh run the make_install script and the module should load when it's doing a test run. Now you can also modprobe it after copying it to /lib/modules/<kernel>/misc/

---

### Post by caracho on 2005-03-16
No, the driver doesn't load anyway....

---

