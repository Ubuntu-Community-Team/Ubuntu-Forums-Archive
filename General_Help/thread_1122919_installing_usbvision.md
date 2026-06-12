---
title: "installing usbvision"
date: 2009-04-11
forum: General Help
---

### Post by joni8.10 on 2009-04-11
In the read me file for usbvision it says: 

In the usbvision directory do
   make; make install; modprobe usbvision


But I don't know where the usbvision directory is or what I'm supposed to do with this information. Could someone give me step-by-step instructions. I'm a beginner.

---

### Post by geraldm on 2009-04-11
It appears that  you have source code to the usbvision package.
In the directory where you unpacked and untarred the package, most packages will create a top directory.  You should change into the top directory just created.
That is the directory where you issue the "make; make install; ..."
I am guessing that after the make there should be a file in that directory named "usbvision.ko", which is what is needed for the "sudo modprobe usbvision"

You need to have installed the compilers from the build-essentials package.
There is information in the stickies for installing that.

regards,
Gerald

---

### Post by joni8.10 on 2009-04-13
> **geraldm said:**
> It appears that  you have source code to the usbvision package.
In the directory where you unpacked and untarred the package, most packages will create a top directory.  You should change into the top directory just created.
That is the directory where you issue the "make; make install; ..."
I am guessing that after the make there should be a file in that directory named "usbvision.ko", which is what is needed for the "sudo modprobe usbvision"

You need to have installed the compilers from the build-essentials package.
There is information in the stickies for installing that.

regards,
Gerald

Gerald, 
I downloaded the tar file to my desktop and extracted it to my desktop. So if I open a terminal, and want to install this thing, what do I type? Please remember I am a beginner. I don't know what compilers are or where the build-essentials package is----or where the stickies are that you mention. Where are the stickies?

---

