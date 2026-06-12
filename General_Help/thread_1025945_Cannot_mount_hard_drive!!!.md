---
title: "Cannot mount hard drive!!!"
date: 2008-12-30
forum: General Help
---

### Post by fitheangel on 2008-12-30
Hiya I'm really new to Ubuntu so a lot of the commands and stuff confuse me! so if you can help i'll be really greatfull if you can explain what i need to do!

Basically, windows has stopped working on my laptop (acer aspire 5920) and so i'm using Ubuntu from a disk in order to access my hard drive and copy my work onto my external hard drive so I can reset windows and not lose any of my work.

But i seem to have come across a common problem, i cannot open my hard drive, i.e it wont mount and neither will my external hard drive

I've tried numerous commands and tried the step by step to mounting volumes on the ubuntu page, but it says Permission Denied!

I've been trying so many different ways for hours and hours looking at forum after forum and i'm still getting no where!! 

Please help! its so frustrating!!!!

Thank you!!!

---

### Post by Coreigh on 2008-12-30
First the external drive. I am guessing it is USB. Unplug it from the computer. THEN start the computer with the LiveCD. Give it plenty of time to start up and get everything running. THEN plug in the external drive. Ubuntu should "see" it and auto mount it.

The internal drive may be a bigger problem. If Windows did not shut down properly the last time then Ubuntu considers it "dirty" and will not mount it. This is a security measure to protect your files. If you can boot in to Windows, let it start up fully, then do a proper shutdown. Try the LiveCD again, if everything is 'ok' the LiveCD should auto mount it or at least make it available in the "Places" menu. If you can not start Windows normally there are ways to "force" the mount but; A) I don't know how and B) this puts your files at greater risk. It may be better to take the hard drive out, put it in a working Windows computer and copy your files to the external drive.

Good luck.

---

### Post by fitheangel on 2008-12-30
Thank you for your help! but i cannot access windows at all! so i think i need to force it!

But you said something about taking my hard drive out? how would i go about doing that?

thank you!

---

### Post by Coreigh on 2008-12-30
That is not something I can easily explain. It is a simple enough matter to take one out but not to put two in one computer. You need to make sure the primary drive is the one from the 'good' computer and the secondary or slave is the one from the bad computer. It will be much easier and safer to get someone to help, or even to take it to a tech. shop and pay someone to do it.

---

