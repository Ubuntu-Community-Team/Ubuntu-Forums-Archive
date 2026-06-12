---
title: "C header files"
date: 2006-06-06
forum: Desktop Environments
---

### Post by srunni on 2006-06-06
Does anyone know what the default location of the directory of C header files that match the kernel is?

I'm trying to install VMware tools in Dapper Drake and I need to know this for the installation. The program suggests the location /usr/src/linux/include, but when I attempted to use it, I found out that the directory didn't even exist. I really need to the path name of the actual directory.

Thanks :o

---

### Post by srunni on 2006-06-06
Anybody know?

---

### Post by mlind on 2006-06-06
You probably need to install linux-kernel-headers package.

```

sudo aptitude install linux-kernel-headers

```

---

### Post by srunni on 2006-06-06
I tried that and the directory /usr/src still has not files in it :-(.

Does anyone else know what's going on?

---

### Post by mlind on 2006-06-06
You do have linux-source package installed?

you may also need to create a symbolic link /usr/src/linux 
that points to your kernel source folder.

---

### Post by az on 2006-06-06
...or just use the linux-headers for your kernel

install the linux-headers-386 package (if you are running 386)

That creates everything you need.  Otherwise, you will have to unpack th ekernel source, config it, compile and install it and then compile your extra module.

---

### Post by srunni on 2006-06-06
So if I install the linux-headers-386, what is the pathname of the directory that it is installed at?

---

### Post by az on 2006-06-07
[QUOTE=srunni]So if I install the linux-headers-386, what is the pathname of the directory that it is installed at?[/QUOTE]
/usr/src/linux-headers-XXXXX

and that is symlinked  to /usr/lib/modules/(kernle version)/build  and that is what most source packages will look for to compile a module.  You shouldn'T need to specify anything.  It should find it by default.

---

