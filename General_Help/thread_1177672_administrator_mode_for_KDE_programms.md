---
title: "administrator mode for KDE programms"
date: 2009-06-03
forum: General Help
---

### Post by JanvL on 2009-06-03
Hi

I have 9.04 installed with KDE 4.2

However if I start the system-setting-programm I do not get the button to change to administrator mode.

What could be missing?

Or how do I start a programm from the menu with administrator rights, I do not mean sudo or su, I know how to handle them but the simple point-and-klick as I did in KDE 3.5.10.

Would be gratefull for a hint because I really start to like kde 4.2.

Regards,
Jan van Leeuwen

---

### Post by McNils on 2009-06-03
> However if I start the system-setting-programm I do not get the button to change to administrator mode.
 
 What could be missing?

You are not missing anything. Most things in system settings does not need root privileges. The one that do will ask you for your password.

> Or how do I start a programm from the menu with administrator rights, I do not mean sudo or su, I know how to handle them but the simple point-and-klick as I did in KDE 3.5.10.
 
 Would be gratefull for a hint because I really start to like kde 4.2.

This looks like something that can't be done. At least I could not find a way (and I tried both the default launcher and classic besides lancelot). You can  edit the menu and add an item that is runned as an other user...

---

### Post by doas777 on 2009-06-03
> **McNils said:**
> You are not missing anything. Most things in system settings does not need root privileges. The one that do will ask you for your password.



This looks like something that can't be done. At least I could not find a way (and I tried both the default launcher and classic besides lancelot). You can  edit the menu and add an item that is runned as an other user...

I use gnome, so take this for what it's worth.
the command (or is that kommand) for kde to run with admin is 'kdesu'.
if i want a launcher to execute with admin, I just edit the launcher command and put 'kdesu ' in front of the application call. then it will prompt for password before launching.

---

### Post by McNils on 2009-06-03
It's **kdesudo** not kdesu.

---

### Post by JanvL on 2009-06-05
Thank you all for reacting or is it reakting?

I have been using linux for quite some years now and I am not sure if I like the way (K)ubuntu is dealing with root-rights in the new versions.
The idea fron KDE 3.5.10 on 8.04 where one can make a choice to change things a an administrator (root) is to my opinion the better way to go. In the end each user of a linux system has to learn what root means if he want to use the system a little more then just browsing/emailing/wordprocessing.

As for KDE 4.2 it has a lot of potential that I have not seen yet but looking forward to find out.
For production however I choose 9.04 with KDE 3.5.10 and wondered that 9.04 still had little problems that belong to the alpha stadium like the MySQL server not starting at boot due to a timing-problem.

Regards,
Jan van Leeuwen

---

### Post by maflynn on 2009-06-05
> **JanvL said:**
> 
The idea fron KDE 3.5.10 on 8.04 where one can make a choice to change things a an administrator (root) is to my opinion the better way to go. In the end each user of a linux system has to learn what root means if he want to use the system a little more then just browsing/emailing/wordprocessing.

That kind of goes against the grain of how current modern day OSs are handling security. For instance, OSX prompts you for a password when installing applications.  You need to use sudo/kdesudo to gain [write] access to certain files and that's the safest approach.  While this slows down the person who's used Linux for quite long time, it shouldn't stop them.  I frequently start up a kate or dolphin session via kdesudo when needing root privilages.  I typically have one ore more termain sessions open anyways so its no big deal

---

