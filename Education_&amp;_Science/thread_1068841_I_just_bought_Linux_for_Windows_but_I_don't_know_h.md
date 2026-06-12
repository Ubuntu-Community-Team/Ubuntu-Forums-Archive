---
title: "I just bought Linux for Windows but I don't know how to install"
date: 2009-02-13
forum: Education &amp; Science
---

### Post by shateredsoul on 2009-02-13
HI everyone,

I have the Spss 16 for Linux, but I dont' even know how to do the basic installation.  Do I click on a certain file? I tried following the instructions on the install pdf for ocdb... but yeah.  I don't get it. I tried looking, I tried reading, I know I'm a newb, but I did try for the last day to install it on my own before asking for help.

So, can someone help me but explaining how to install the program? I did find the post on how to fix the problems once installed, i'm just trying to do a basic install first.

thanks!

---

### Post by shateredsoul on 2009-02-13
I'm using Ubuntu (the newest one)

---

### Post by gunksta on 2009-02-13
If you look in this forum, there is a thread on installing SPSS 16 on Ubuntu.

Disclaimer: I have never installed SPSS (any version) on Linux.

But, the first question seems pretty obvious. When you pop the CD into the CD-ROM, what do you see? In other words, I want to know what is on the CD, such as the files, directory structure, etc. I'm sure it's not too hard.

---

### Post by shateredsoul on 2009-02-13
Well I did find directions.. but it asks me to change the directory (the directions are to use a terminal).  I don't know how to change the terminal.  It also said you can copy the .bin file locally then change it's permission to executable so I tried that.  I copied the bin file to my desktop, right clicked it, set it to executable.  But then it ubuntu say that the file format is not recognized. Any ideas?

---

### Post by shateredsoul on 2009-02-13
Ok, I figured how to change the directory to the cdrom... the install guide says to type in "./setup.bin" but it doesnt work.  The cd does have a file with that name... so i'm not sure why it's not working.

-Laptop:/$ cd cdrom
-Laptop:/cdrom$ ./setup.bin
bash: ./setup.bin: No such file or directory
-Laptop:/cdrom$ /setup.bin
bash: /setup.bin: No such file or directory
-Laptop:/cdrom$ /setup.bin
bash: /setup.bin: No such file or directory
-Laptop:/cdrom$ setup.bin
bash: setup.bin: command not found
-Laptop:/cdrom$ ./setup.bin
bash: ./setup.bin: No such file or directory
-Laptop:/cdrom$

---

### Post by linuxisevolution on 2009-02-13
> **shateredsoul said:**
> Well I did find directions.. but it asks me to change the directory (the directions are to use a terminal).  I don't know how to change the terminal.  It also said you can copy the .bin file locally then change it's permission to executable so I tried that.  I copied the bin file to my desktop, right clicked it, set it to executable.  But then it ubuntu say that the file format is not recognized. Any ideas?

Right click the file and rename it to something you can remember, without spaces, and keep the .bin. Make sure you have permissions to it ( right click, properties, permissions tab). Then, click Applications >> Accessories >> Terminal. Type "cd ~/Destop" without quotes. Then, type "sudo" without quotes and then the name of the file with the .bin part.


EDIT: copy the files to your desktop first.

---

### Post by linuxisevolution on 2009-02-13
I see. Try running it from the cdrom but like this:

setup.bin 

instead of

./setup.bin


This confuses me and I haven't seen it before. I have only seen:

./configure

with the ./ part and no .bin. Odd... Who makes this software anyway? Just curious..

---

### Post by shateredsoul on 2009-02-14
thanks everyone it worked... tooks sooo long

---

