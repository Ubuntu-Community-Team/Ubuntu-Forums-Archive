---
title: "Boot up problems?"
date: 2008-02-27
forum: Desktop Environments
---

### Post by Shnap on 2008-02-27
I just installed Ubuntu and I am having some problems.

First, I have two hard drive's I wanted Ubuntu to install on a smaller one that I don't currently have windows on. I am not sure that it installed on there. When I restart I get prompted to select where I want to boot from (Floppy, Disk drive, Hard Drive 1, Hard drive 2 (the smaller one)) When I select hard drive 2 it comes up with "No operating system found". So I restart and select the other hard drive, it then goes to a menu asking witch OS I want to boot into. (Ubuntu and Windows XP), I don't want this, I am not the only one using this computer and my parents wont be happy having to do that every time they restart, AND my wireless key bored does not work in that menu, I have to use a USB one.

I was just hoping to install Ubuntu on the smaller hard drive and go into the BIOS and select the other drive to boot into Ubuntu when I wanted to use it.

So basically, How do I know what hard drive it installed on? How do I not get the menu asking witch OS to start up in.

Also when I am in Ubuntu my internet doesn't work, I have a linksys wmp54g wireless card.

Help?!

Thanks, 
Shnap

---

### Post by geekcliff on 2008-02-27
Try this link it helped me. [http://ubuntuforums.org/showthread.php?t=228104&highlight=grubed&page=24](http://ubuntuforums.org/showthread.php?t=228104&highlight=grubed&page=24)
You'll need to type sudo bash ./install to install this program, they missed out the bash bit in the readme.

---

### Post by Shnap on 2008-02-27
So I have to do that in Ubuntu right? But how will I download it in there I can't get a internet connection.

---

### Post by geekcliff on 2008-02-27
you can download it in windows, thats what i did, then put it on a usb stick.

---

### Post by Shnap on 2008-02-27
Okay So I put that program on a flash drive. When I go to Run it in the Terminal, I get a "No such file or directory" message.

Good news!, I got my internet working!

---

### Post by Shnap on 2008-02-27
Help?! I still can't get that to work.

---

### Post by geekcliff on 2008-02-28
Unzip the download and read the instructions inside, then you'll have to cd to the folder you created when you unzipped it, if its on the desktop it should be something like cd ./Grubed, this is case sensetive. then run the install script i gave you before.

---

### Post by geekcliff on 2008-02-28
I've just found something in another thread that much easier,now that you got internet connection,go to synaptic package manager in system/administration and search for StartUp-Manager, i've just tried it myself its great, 10 times easier, you'll find in system/administration again after its installed. 
Good luck.:guitar:

---

