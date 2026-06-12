---
title: "Make Error"
date: 2005-05-06
forum: Desktop Environments
---

### Post by Amdmhz on 2005-05-06
HI all. I am still a new linux user trying to get better. I need to run make so that I can load a driver but it is giving me this error and I don't know what I am suppose to do. Can anyone help me out on this. I searched the forums but it didn't help.

make: *** No rule to make target `/usr/src/linux-2.6.10-5-386/drivers/usb/serial/usb-serial.h', needed by `usb-serial.h'.  Stop.


Thanks

---

### Post by Amdmhz on 2005-05-06
Hi all.. I have been messing with this for a while and googling it. I still can't find an answer of what to do. Can anyone give me a hint,  :smile: 

Thanks

---

### Post by lorap on 2005-05-06
hi friend.
you aren't alone.
i'm searching for the solution for your equation.
wait,all you've to do :-)
i've a book "running linux",it'd be there...

---

### Post by kosmic on 2005-05-06
see if you have the Kernel sources in the /usr/src/linux-2.6.10-5-386 directory if there is no files inside that directory or the directory does not exist, then you need the kernel sources to compile the program.


hope it helps

---

### Post by lorap on 2005-05-06
i've found a lot of materials so the only thing i need to know what files you've cause as i see it's a header file written in C programming language.
tell me what files and how many you've.
did you build this makefile yourself or was it supported with source files ?
explain all this to me.
you may write to my private email:
[email]prianfamily@gmail.com[/email]

---

### Post by Amdmhz on 2005-05-06
Hi.  If i do an apt-get install kernel-source it downloads this:

kernel-source-2.4.27.tar.bz2

Hmmm.. I don't understand why it would downlaod an older kernel. It looks like I need the newer kernel to be able to make this file, is this correct> 

Anyway, this is what I have in my /usr/scr diectory

amdmhz@Laptop:/usr/src$ ls
kernel-source-2.4.27.tar.bz2  modules  ndiswrapper-source.tar.gz 

Thanks

---

### Post by lorap on 2005-05-07
hi friend.
in your make file the files you unpack are built in specific consequence,you know some files may depend on others.
you just simply can open this make file with gedit or other text editor and look inside.
there should be something like this:
gcc anyfile.c
but this file either is at different location or missing at all.
what could be the case too.
but could be something other.
say your makefile has some types of compilation and building the sources then as a parameter it may receive the name of the main file as the key to go by but you don't pass it (probably the name of some of the files extracted).cause you know they could create this make file the way you can build not only application but few so once you pass it the application name it knows how to build it.
let me know if i was right.

---

