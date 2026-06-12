---
title: "Qemu: Windows XP error programs are not valid win32"
date: 2008-06-23
forum: Desktop Environments
---

### Post by Gaming4JC on 2008-06-23
Hello,
I installed qemu and qemu launcher onto my Ubuntu Hardy. Then I installed Windows XP on the virtual environment, it worked fine on install and runs perfectly on everything else except for this...

The problem is when I click on any windows executable (.exe), it gives me the error message: This is not a valid win32 application.

I heard an error like this was on qemu version 8 this is ver 0.9 with latest repositories soo....

If anyone knows about this, let me know. :)

---

### Post by Gaming4JC on 2008-06-24
Windows 98SE works fine except it cannot connect to the internet. I shall try some drivers over here and post if it works: [http://www.claunia.com/qemu/drivers/index.html](http://www.claunia.com/qemu/drivers/index.html)

Although I can run Win98SE, I really need WindowsXP for most applications. Would anyone know about this win32 error? It doesn't appear on Win98SE... O_o

---

### Post by Gaming4JC on 2008-06-25
Eurika! The fix was to reinstall Windows XP again. I gave it 1GB memory this time and 3.5GB on the hard drive. Also, it seems to be a bug with large CDs. Any CD containing over 10 files will some times trigger a win32 bug error.

Anyhow, works for me. Now I can run a few Windows Apps ^_^

---

### Post by larryfroot on 2008-07-07
Having the same problem in virtualbox...I blamed virtualbox at first - but yes...sorry virtualbox its a windows bug. A virtualised windows bug, but still one of Redmond's sneakies. 

Am installing another VM to see if my brainwave is a brainwave or an act of density. Have seen though that copying the CD contents to a folder on your hard drive and installing it from there works. Wish I found out about that trick before I started an install into my second VM...we learn.

---

### Post by javad-r on 2010-08-17
Hi 
If you just cant run a program from your CD/DVD drive, 
go to setting->storage , remove CD/DVD drive and add it again. 
I hope it solve your problem.

---

### Post by Gaming4JC on 2011-04-12
Ran into the problem again, but resolved it by mounting an .iso in VBox instead of the actual CD. Strange bug, whatever it is.

---

