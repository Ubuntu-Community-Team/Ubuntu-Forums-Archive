---
title: "Ubuntu Studio"
date: 2007-07-31
forum: Desktop Effects &amp; Customization
---

### Post by fazavon on 2007-07-31
Alright, I'm not sure if I am in the right place, but here goes. 

i installed the Ubuntu Studio on top of 7.04. All is well until I try to right click on my desktop, nothing happens, and every time I reboot or shutdown, I makes my Desktop background this weird blue colour and the default has been changed to a gray colour. 

Again I am not sure if I am in the right place to ask this one, if not please let me know.

thanks

//j

---

### Post by Immolatus on 2007-07-31
Witch 7.04 is ubuntu studio over ubuntu or kubuntu? If it's kubuntu you need to remove KDM.
 If it's ubuntu you need to make sure you have ubuntu studio desktop installed.
so do:

sudo apt-get install ubuntustudio_desktop

see what happens. I'm assuming you installed ubuntu studio from switching the repos. instead of using the disk, as I have done this before myself but it was ubuntu-->ubuntustudio, no problem.

---

### Post by fazavon on 2007-07-31
No I had done that. 

And out of no where it just started working, like an hour later??? not sure why or how, but I am not going to fight it.

Thank you for replying

//j

---

### Post by Geowilky on 2008-03-08
> **Immolatus said:**
> Witch 7.04 is ubuntu studio over ubuntu or kubuntu? If it's kubuntu you need to remove KDM.
 If it's ubuntu you need to make sure you have ubuntu studio desktop installed.
so do:

sudo apt-get install ubuntustudio_desktop

see what happens. I'm assuming you installed ubuntu studio from switching the repos. instead of using the disk, as I have done this before myself but it was ubuntu-->ubuntustudio, no problem.



Is this working

---

### Post by Geowilky on 2008-03-08
> **Immolatus said:**
> Witch 7.04 is ubuntu studio over ubuntu or kubuntu? If it's kubuntu you need to remove KDM.
 If it's ubuntu you need to make sure you have ubuntu studio desktop installed.
so do:

sudo apt-get install ubuntustudio_desktop

see what happens. I'm assuming you installed ubuntu studio from switching the repos. instead of using the disk, as I have done this before myself but it was ubuntu-->ubuntustudio, no problem.





I've been trying to find out how to Upgrade Ubuntu 7.10 64 to Ubuntustudio 64.  I tried doing the sudo command line stuff without a possitive result to this point..


george@DualCoreRed1:~$ sudo apt-get install ubuntustudio_desktop
[sudo] password for george:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntustudio_desktop

Can someone help me?

---

