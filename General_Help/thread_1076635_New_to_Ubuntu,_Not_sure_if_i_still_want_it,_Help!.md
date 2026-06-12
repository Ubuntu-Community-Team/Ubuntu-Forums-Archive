---
title: "New to Ubuntu, Not sure if i still want it, Help?!"
date: 2009-02-21
forum: General Help
---

### Post by XzDarkStarzX on 2009-02-21
Before i decide whether or not to toss this OS out the window, i need to know a few of things from whom ever can help:

1) Can i Run Photoshop CS3 or CS4? (es, My company requires I use that program, not a look-alike. Also, i do simply just like them)

2) Can i run MS Office 2007?

3) Is there any solution for making my iPod work with 8.10?

4) What is the difference between Fendora 10 & 11 and Ubuntu 8.10?

Thank you all in advance!!!
-DS

---

### Post by scottuss on 2009-02-21
Yes you can run Office 2007, you need to install an application called WINE which will allow you to run Windows software on Linux. You could also try this for Photoshop, although I'm not sure if it will work (I don't use Photoshop, certainly not when GIMP does pretty much the same thing)

And which iPod do you have?


If you plug it in and load the Music Player application (Rhythmbox) it should show up there, much like iTunes

---

### Post by Thowsen on 2009-02-21
take it easy , these problems can all be solved, maybe Im not the right guy to answer but i'll try.

You can run photoshop via wine. thats no problem
you can install wine via  '' sudo apt-get install wine '' in console i think

you can run office too. by google'in for like 20sec i found this guide
[http://helpforlinux.blogspot.com/2008/12/install-microsoft-office-2007-in-ubuntu.html](http://helpforlinux.blogspot.com/2008/12/install-microsoft-office-2007-in-ubuntu.html)

n by googleing for like 10sec more i found this thread.
[http://ubuntuforums.org/showthread.php?t=455842](http://ubuntuforums.org/showthread.php?t=455842)

hope it'll help you.

---

### Post by Mercury_Alpha on 2009-02-21
> **XzDarkStarzX said:**
> Before i decide whether or not to toss this OS out the window, i need to know a few of things from whom ever can help:

1) Can i Run Photoshop CS3 or CS4? (es, My company requires I use that program, not a look-alike. Also, i do simply just like them)

2) Can i run MS Office 2007?


You can install Windows in a virtual machine to run CS and MS Office. As long as you're not manipulating huge image files in CS (50+ MB) you should be fine. Ubuntu comes with VirtualBox OSE, but I recommend removing it and installing [Sun xVM VirtualBox]("http://www.virtualbox.org/wiki/Linux_Downloads"). I recommend having a least 1GB of system RAM if you want to run Windows in a VM smoothly.

> 
3) Is there any solution for making my iPod work with 8.10?


There are several Linux apps that work fine with an iPod, like Rhythmbox. If you want access to iTunes music store, however, you'll have to go the VM route mentioned above. If you're having trouble getting Ubuntu to *recognize* your iPod, that's a separate support issue.

Edit: Of course, if you can get these apps to run in Wine, that's much simpler. But iTunes is pretty much a no-go without either running it in a VM or dual-booting.

---

### Post by lukjad on 2009-02-21
> **XzDarkStarzX said:**
> Before i decide whether or not to toss this OS out the window, i need to know a few of things from whom ever can help:

1) Can i Run Photoshop CS3 or CS4? (es, My company requires I use that program, not a look-alike. Also, i do simply just like them)

2) Can i run MS Office 2007?

3) Is there any solution for making my iPod work with 8.10?

4) What is the difference between Fendora 10 & 11 and Ubuntu 8.10?

Thank you all in advance!!!
-DS
@XzDarkStarzX 
WINE is a good idea to check out, but you do know you can dual boot, right? That way you can use Windows for whatever program work dictates you use. Then, for everything else, like surfing the 'net, typing a document, or sending an e-mail, you use Ubuntu.

---

### Post by XzDarkStarzX on 2009-02-21
Thank you every one!

Lol, the cd drive on this machine is a bit spotty, and it took me ages to get a successful install of the OS - then i come to find none of my old expensive oft ware worked! This was a huge help, bless all of ya

-DS

curios though, is ubuntu better than fendora? i was talking to a friend of mine earlier who was thining of using it instead

---

### Post by Deutscher Alex on 2009-02-21
> **XzDarkStarzX said:**
> Before i decide whether or not to toss this OS out the window, i need to know a few of things from whom ever can help:

1) Can i Run Photoshop CS3 or CS4? (es, My company requires I use that program, not a look-alike. Also, i do simply just like them)

2) Can i run MS Office 2007?

3) Is there any solution for making my iPod work with 8.10?

4) What is the difference between Fendora 10 & 11 and Ubuntu 8.10?

Thank you all in advance!!!
-DS

1. If your company REQUIRES Photoshop, then you should stick with a dual boot

2. OpenOffice works fine, but you can use WINE to run MS Office if you want

3. The program gtkpod also works nicely with iPods

---

### Post by s.fox on 2009-02-21
I have used Fedora and Ubuntu.   They are kinda like cousins.  I prefer Ubuntu over Fedora, simply because of the community here.  I don't think its a case of what is better,  more like what you prefer.  I can't really justify why I prefer Ubuntu over Fedora.  Nothing wrong with either of them in my opinion

For a technical comparison,  this [site]("http://polishlinux.org/choose/comparison/?distro1=Fedora&distro2=Ubuntu") isn't too bad.

Sorry I can't be of any more help!

---

### Post by Vince4Amy on 2009-02-21
> 4) What is the difference between Fendora 10 & 11 and Ubuntu 8.10?

Fedora uses RPMs/YUM for package management whereas Ubuntu uses DEBs/APT for package management. They are both well supported and you should be able to find the software you want for both platforms.

Although I prefer Fedora to Ubuntu I would recommend that you do not switch straight away as Fedora uses newer packages than Ubuntu and it could make setting up hardware like Graphics cards more difficult. Fedora does run faster and on less resources than Ubuntu for me though.

---

### Post by mikewhatever on 2009-02-21
I strongly suggest the OP reviews the following thread. I my personal opinion, Ubuntu is not for you.
[http://ubuntuforums.org/showthread.php?t=63315](http://ubuntuforums.org/showthread.php?t=63315)

---

### Post by Mercury_Alpha on 2009-02-21
> **XzDarkStarzX said:**
> Thank you every one!

Lol, the cd drive on this machine is a bit spotty, and it took me ages to get a successful install of the OS - then i come to find none of my old expensive oft ware worked! This was a huge help, bless all of ya

If you're having trouble successfully burning install CDs, sometimes the problem is an aging drive, dirty lens, or faulty data cable. In the short run, you can swap the data cable and get one of those lens-cleaning disks, but you may need to replace the drive.

Alternatively, you can burn your disks at low speed (4x or even 2x). This is usually the best way to go for install CDs, to ensure a minimum of burn errors. You'll also want to compare the MD5 sum on the disk to the one listed online. If the disk MD5 is different, the data did not copy over correctly.

---

