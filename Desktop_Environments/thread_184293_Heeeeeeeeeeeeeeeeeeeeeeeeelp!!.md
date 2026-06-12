---
title: "Heeeeeeeeeeeeeeeeeeeeeeeeelp!!"
date: 2006-05-29
forum: Desktop Environments
---

### Post by Isoss on 2006-05-29
I dunno what happened!! I was downloading some packages using synaptic, some apache and mysql stuff and then rebooted!

I have Ubuntu Breezy with Kubuntu Desktop as a default session

it asks for logins, whatever session I choose, Gnome or KDE, and enter my logins, it refreshes as if preparing to ask for logins when booting and then get's back to the login screen. it doesn't go to the splash screen at all, instead it asks for the logins again! 

I entered the failsafe and then started synaptic, I found that - probable by mistake - that Kubuntu-desktop package is not installed!!! I checked it and reinstalled it. now after it's done I rebooted and it asked for the logins. I entered them and the splash screen appeared, but froze for a while!
Then it gave me an error that I don't have access permission to a some file - sorry I don't remember it's name :confused:  - and then I had to reboot! I entered the the failsafe again and thinking that there is a problem also with the Gnome-desktop I started synaptic and searched for gnome and selected some packages that as far as I remember they were installed before but now they're not! and at the same time I removed kubuntu-desktop and it's dependencies and everything that I installed with. I rebooted after all this mess is done and surprisingly it takes me to a unix shell as if I chose the recovery mode and asks for the logins!!! I can't login into ubuntu or kubuntu ](*,)  ... Please help! I don't wanna reinstall the whole system again cuz that takes a day installing the system and everything I need and had installed!

Thanks in advance ppl.

---

### Post by gingermark on 2006-05-29
It sounds like the old .ICEauthority problem. Kubuntu-desktop is a metapackage that can be removed without problem (if you get rid of one program that comprises it then it will be removed as well), so I think that's probably a red herring.

In the failsafe terminal do ```
sudo chown yourusername ~/.ICEauthority
sudo chmod 777 ./.ICEauthority
``` and see if that helps.

---

### Post by Isoss on 2006-05-29
Yes, that's right, this is the file! but the problem now is that I can't reach to the login screen! I can't infact choose any session or anything! I am in something like Unix shell. no graphics .. I mean like the recovery mode or when in ubuntu you press Ctrl+Alt+Backspace!

---

### Post by gingermark on 2006-05-29
So, in this shell can you not type the commands I gave you? Does that not work?

---

### Post by Isoss on 2006-05-29
Hey .. problem solved!

after removing kubuntu-desktop with synaptic I couldn't reach to the login page as I mentioned. But in the shell I ran: sudo apt-get install kubuntu-desktop and then rebooted and the login page appeared again. Then the same problem occured, that I don't have access to the ICEauthority. I entered the failsafe and ran: ```
sudo chmod 777 /home/isos/.ICEauthority
``` And the magic happened.

Thanks a lot.

---

### Post by gingermark on 2006-05-29
This problem is usually caused by using sudo to start graphical programs.

From [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) :

> **NEVER** use sudo to start graphical programs. You should always use gksudo or kdesu to run such programs, otherwise new login attempts may fail.

---

### Post by Isoss on 2006-05-29
Thanks for the valuable info

---

