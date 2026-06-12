---
title: "driver compiling error"
date: 2008-06-18
forum: Debian
---

### Post by neolin on 2008-06-18
recently i installed debian etch.....i want to compile the driver for my ethernet card....silan sc92031...i have the file needed to be compiled ( the .c file and makefile) provided on the disc included.....i have installed the kernel headers and kernel source package and other dependencies required...but when i run the make command, it says "kernel source not found. stop".......it has worked for a few people but not working for me..please suggest as to what i should do...do i need to compile the .c file in a c compiler like cgcc or what....the readme tells me to run make command.....and make install after the .ko file is generated...any help would be appreciated.......

---

### Post by ibutho on 2008-06-18
You need to install the kernel source package that matches the version of the kernel you are running. In Debian based distros its called linux-source.

---

### Post by neolin on 2008-06-18
i did install the linux source package......but still it gives no kernel source found. stop message

---

### Post by Mizzou_Engineer on 2008-06-19
> **neolin said:**
> i did install the linux source package......but still it gives no kernel source found. stop message

Have you tried using modules-assistant? That is usually the most fail-safe way to compile kernel modules, provided the module you want is in m-a.

---

### Post by benuski on 2008-06-21
I second module-assistant.  As root, type in ```
m-a prepare
``` which should install all of the necessary dependencies, and then type in 

```
m-a a-i <name of the driver>
```
without the carets.

---

### Post by tturrisi on 2008-06-22
Have a look at the install files that accompanies the package or check the make file for setting parameters.  You may need to point to your sources in the script.  example --/usr/src/xxx

---

### Post by neolin on 2008-06-29
thnx ppl. i found another way. after some googling i found that the silan sc92031 drivers have been inbuilt int the linux kernel itself 2.6.21.... etch by default is 2.6.17 i think.......so if i update the kernel, will the card be detected automatically? going to try it

---

