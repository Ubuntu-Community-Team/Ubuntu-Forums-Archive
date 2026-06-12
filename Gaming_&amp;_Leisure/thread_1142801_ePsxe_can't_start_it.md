---
title: "ePsxe_can't start it"
date: 2009-04-29
forum: Gaming &amp; Leisure
---

### Post by demontager on 2009-04-29
I have installed ePsxe on Ubuntu 9.04 x86_64, when i run it, receive this:
```

pal@pal-laptop:~$ epsxe
 * Running ePSXe emulator version 1.6.0. 
./epsxe: symbol lookup error: /lib32/libgdk-1.2.so.0: undefined symbol: g_source_add


```
i put ibgtk1.2_1.2.10-18.1build2_i386.deb (extracted libgdk-1.2.so.0)  to /lib32 , but it not work as should, please help.

---

### Post by Dark Aspect on 2009-04-29
> **demontager said:**
> I have installed ePsxe on Ubuntu 9.04 x86_64, when i run it, receive this:
```

pal@pal-laptop:~$ epsxe
 * Running ePSXe emulator version 1.6.0. 
./epsxe: symbol lookup error: /lib32/libgdk-1.2.so.0: undefined symbol: g_source_add


```
i put ibgtk1.2_1.2.10-18.1build2_i386.deb (extracted libgdk-1.2.so.0)  to /lib32 , but it not work as should, please help.

We have an understanding without a solution.

[http://ubuntuforums.org/showthread.php?t=1137345]("http://ubuntuforums.org/showthread.php?t=1137345")

---

### Post by Grishka on 2009-04-29
> **demontager said:**
> I have installed ePsxe on Ubuntu 9.04 x86_64, when i run it, receive this:
```

pal@pal-laptop:~$ epsxe
 * Running ePSXe emulator version 1.6.0. 
./epsxe: symbol lookup error: /lib32/libgdk-1.2.so.0: undefined symbol: g_source_add


```
i put ibgtk1.2_1.2.10-18.1build2_i386.deb (extracted libgdk-1.2.so.0)  to /lib32 , but it not work as should, please help.

extract all four files. so.0 is just a symlink. you may also need a 32-bit version of libglib1.2. again, extract all library files.

---

### Post by demontager on 2009-04-30
i get 
```

pal@pal-laptop:~/Games/epsxe$ ldd epsxe
    not a dynamic executable
pal@pal-laptop:~/Games/epsxe$ file epsxe
epsxe: ELF 32-bit LSB executable, Intel 80386, version 1, statically linked, corrupted section header size
pal@pal-laptop:~/Games/epsxe$ 

```
why i can't see dependencies?
And i put libgdk-1.2.so.0.9.1 to /usr/lib32, but receive same error, libgdk-1.2.so.0 symlink to it.

---

### Post by Grishka on 2009-04-30
> **demontager said:**
> i get 
```

pal@pal-laptop:~/Games/epsxe$ ldd epsxe
    not a dynamic executable
pal@pal-laptop:~/Games/epsxe$ file epsxe
epsxe: ELF 32-bit LSB executable, Intel 80386, version 1, statically linked, corrupted section header size
pal@pal-laptop:~/Games/epsxe$ 

```
why i can't see dependencies?
And i put libgdk-1.2.so.0.9.1 to /usr/lib32, but receive same error, libgdk-1.2.so.0 symlink to it.

I'm getting the same ldd and file output, but epsxe works for me. this must be irrelevant. but look here: [https://www.linuxquestions.org/questions/linux-software-2/relocation-error-in-libgdk-1.2.so.0.-undefined-symbol-gsourceadd-409461/](https://www.linuxquestions.org/questions/linux-software-2/relocation-error-in-libgdk-1.2.so.0.-undefined-symbol-gsourceadd-409461/). maybe you're having the same issue as that guy. if not, try playing around with ltrace.

---

### Post by Dark Aspect on 2009-04-30
> **demontager said:**
> i get 
```

pal@pal-laptop:~/Games/epsxe$ ldd epsxe
    not a dynamic executable
pal@pal-laptop:~/Games/epsxe$ file epsxe
epsxe: ELF 32-bit LSB executable, Intel 80386, version 1, statically linked, corrupted section header size
pal@pal-laptop:~/Games/epsxe$ 

```
why i can't see dependencies?
And i put libgdk-1.2.so.0.9.1 to /usr/lib32, but receive same error, libgdk-1.2.so.0 symlink to it.

Try

```
sudo apt-get install upx-nrv

```

and than

```
upx -d ~/epsxe/epsxe
```

make a backup first, I have tired both the compressed and uncompressed excutable. Is there any idea why I get a segmentation fault?

I have all of the libraries satisfied in terms of lib32? symlinked and everything, I have no idea why it doesn't run. What is ltrace and how do I play around with it?

---

### Post by Grishka on 2009-04-30
> **Dark Aspect said:**
> Try

```
sudo apt-get install upx-nrv

```

and than

```
upx -d ~/epsxe/epsxe
```

make a backup first, I have tired both the compressed and uncompressed excutable. Is there any idea why I get a segmentation fault?

I have all of the libraries satisfied in terms of lib32? symlinked and everything, I have no idea why it doesn't run. What is ltrace and how do I play around with it?

ltrace will tell you what files the application is trying to use, you can use it to see where exactly the problem lies.

---

### Post by Dark Aspect on 2009-04-30
> **Grishka said:**
> .....but epsxe works for me.....

Ok I am going to try to find the problem on my system, can you tell me if you are using a compressed or uncompressed executable?

---

### Post by Grishka on 2009-04-30
> **Dark Aspect said:**
> Ok I am going to try to find the problem on my system, can you tell me if you are using a compressed or uncompressed executable?

I'm using a completely unmodified binary. it worked almost out of the box for me.

---

### Post by wingnux on 2009-05-08
I get this error when trying to run epsxe on Jaunty 64bit:

> ./epsxe: error while loading shared libraries: libgmodule-1.2.so.0: cannot open shared object file: No such file or directory


Trying to get the lib with getlibs:
> 
wingnux@wingnux-desktop:~/Downloads/epsxe$ getlibs -32 libgmodule-1.2.so.0
libgmodule-1.2.so.0: libglib1.2
The following i386 packages will be installed:
libglib1.2
Continue [Y/n]? y
libglib1.2 was not found in your repositories
Make sure you have all repositories enabled and updated
No packages to install

---

