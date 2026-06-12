---
title: "Can't login, Hard drive full."
date: 2007-04-23
forum: Desktop Environments
---

### Post by Mechanist on 2007-04-23
Hello i am very new to ubuntu and need some help. I am no longer able to log into ubuntu . It tells me that the hard drive is full. I have no idea what to do to be honest. I am currently writing this from the live cd. A simple(if possible) walk through would be great. thx :confused:

---

### Post by Mechanist on 2007-04-23
if it helps i can see the hard drive thats full from computer. is there any way i can delete from this. It says i dont have permission.

---

### Post by MikeDX on 2007-04-23
Booting from the live cd is a great start

there should be an icon on your desktop called file system (I think, from memory)

I doubt if you need to delete a lot of files, but it sounds like something has gone a bit wrong! What size hard drive is it? I only have a 30gb in this laptop and that works fine, i've yet to fill it up.

You could try deleting or backing up some stuff from /home/(your username) and see if there is anything in /tmp

if you arent sure about anything, copy the files onto another place on the network or a usb stick

Good luck

---

### Post by amac777 on 2007-04-23
At the graphical login screen, press CTRL-ALT-F1 to login using the console. Unlike the graphic login screen, the console should still let you login even if the harddrive is full.

Once you're in, delete some files to clear up space.

Try:

sudo apt-get clean

and that should free up some space.

---

### Post by Mechanist on 2007-04-23
thx its working now, cheers for your help. So easy to fix wow :guitar:

---

