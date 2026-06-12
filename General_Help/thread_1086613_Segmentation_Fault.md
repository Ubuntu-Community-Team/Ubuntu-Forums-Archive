---
title: "Segmentation Fault?"
date: 2009-03-04
forum: General Help
---

### Post by wolfman1221 on 2009-03-04
Firefox keeps closing on me when I am in the middle of my work. When I ran it in terminal, I received a message that said "segmentation fault". Does anyone know how to fix this?


 Also, does anyone know how to get ubuntu up and running at a fast rate? I've just started using it(I am a newbie), and it seem to run alot slower than windows.

---

### Post by 3rdalbum on 2009-03-04
The message "Segmentation Fault" just means "the program crashed". Have you got Flash 10 installed? If you are using 64-bit, have you got the 64-bit version of Flash 10 installed?

Sometimes, using an unofficial Flash player can cause Firefox crashes. Otherwise, if you're only getting the Segfault message, you could try another browser like Epiphany.

As for the speed problem, you should check to see that you have 3D graphics support. If your computer has Intel graphics, then you already have 3D support. If your computer has Nvidia or ATI, then you need to install a driver to get 3D support. This will speed up all window management, which makes the computer feel a lot faster.

Also, Ubuntu 8.10 really needs 1 gigabyte of RAM to run fast on a 32-bit operating system, or 2 gigabytes to run fast on a 64-bit operating system. It's not like Ubuntu 8.10 was released eight years ago to run on machines with 128 megabytes of RAM :-)

---

### Post by wolfman1221 on 2009-03-04
I have adobe flash player 10 installed.

---

### Post by lykwydchykyn on 2009-03-04
> **3rdalbum said:**
> 
Also, Ubuntu 8.10 really needs 1 gigabyte of RAM to run fast on a 32-bit operating system, or 2 gigabytes to run fast on a 64-bit operating system. It's not like Ubuntu 8.10 was released eight years ago to run on machines with 128 megabytes of RAM :-)

1 gig?  I guess it depends on your definition of "fast", but I run Ubuntu just fine on 512 MB.  More than likely this is an issue with the video drivers.

wolfman, can you post the specs of your machine, particularly the graphics card information?

also, can you try this:
```

firefox -safe-mode

```
and see if firefox will run.

---

