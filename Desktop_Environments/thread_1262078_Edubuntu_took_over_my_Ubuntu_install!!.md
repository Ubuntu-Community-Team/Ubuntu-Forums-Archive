---
title: "Edubuntu took over my Ubuntu install!!??"
date: 2009-09-09
forum: Desktop Environments
---

### Post by p4nth30n on 2009-09-09
I am really hoping that i can get some help here. I have been running Ubuntu 9.04 on my system. It runs great and i love it, something very odd happened today that has me wondering if i have been hacked, tricked, or both? Or have i just lost my mind? LOL Heres the scoop. A few days ago i installed some educational software for math and science to keep my skills up since i have been out of school for a long time now.  The install through "Add/Remove" went fine seemingly, then today while i was watching a DVD my "update manager" popped up saying i had updates, so as usual i clicked update and went back to watching my movie. When i finished my movie, i noticed that the update manager was stuck in the same position that it was in when i started the movie. I tried to close it and it would not close so i figured a reboot would solve the issue. Upon reboot, i was greeted with the Edubuntu login screen!? Having NOT installed Edubuntu i was wondering how this happenedi logged in and my entire theme was gone and replaced with Edubuntu and i had a bunch of educcational software for KDE which was even wierder because i use Gnome, not KDE. I opened the terminal and used the command "sudo apt-get remove edubuntu-desktop" it did its usual, and seemed to work. I rebooted again hoping to see my regular login screen and again i got the edubuntu login screen, i logged in and saw all of the same edubuntu software still in place, nothing was actualy removed? Edubuntu took over my system without permission, without my having installed it, and it wont come off of my system!!
Two questions..
1. has this happened to anyone else?
2. How do i get my system back to the regular Ubuntu Jaunty without wiping the whole thing again and reinstalling from scratch?
 Its not that i have any problem with edubuntu, but i have a seriouse problem with my computer doing things that were never asked of it. THAT is the main reason i switched from Windoze to begin with..Someone please help


Chris  :confused:

---

### Post by hellmet on 2009-09-09
May we know what you installed? Something might have triggered the installation of edubuntu-desktop. Also, one or more of those educational programs you installed might have actually been a KDE app, so you got KDE libs too.

---

### Post by ugm6hr on 2009-09-09
Sounds like one of the applications you were intending to install triggered edubuntu-desktop to install.

Can't think which, since edubuntu-desktop shouldn't be a dependency of anything.

The majority of the educational software is KDE-based, so te fact that you use Gnome is irrelevant.

To remove, you probably need to get rid of the artwork:
```
sudo apt-get remove edubuntu*
```

---

### Post by p4nth30n on 2009-09-09
Im wrecked, now i cant get to my home folder, or any other for that matter. Sorry that i dont remember the name of the programs that i installed for math and science, but i dont have them in my list and cant bring them up anyway. I know that they didnt start with K as is often the nomenclature for KDE programs. when i use command line to remove them it gives me this
p4nth30n@p4nth30n-desktop:~$ sudo apt-get remove edubuntu
[sudo] password for p4nth30n: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package edubuntu
p4nth30n@p4nth30n-desktop:~$ 
 but when i click on my "system menu it still says "about ubuntu" AND "about edubuntu"

When i try to go to any folder, e.g. home, music, documents it tells me that no application is registered as handeling the file???  My bandwidth is So limited that these forum pages take like a full minute to load and there are no other applications running.

I thank you both for trying to help but i am just going to reinstall the whole OS and be more careful about trying out new packages..LOL

---

### Post by ugm6hr on 2009-09-10
> **p4nth30n said:**
> p4nth30n@p4nth30n-desktop:~$ sudo apt-get remove edubuntu

You missed the * (star) at the end.

---

### Post by hellmet on 2009-09-10
paste the output of 
sudo dpkg --get-selections | grep edubuntu

---

### Post by p4nth30n on 2009-09-10
thanks again for all of your willingness to help. 

I have already reinstalled jaunty and i am now up and running fine. I noticed just after my last post that i missed the wildcard,(star) after my last attempt at a terminal command. much appreciation to you both.

---

### Post by Scott M. Sanders on 2009-10-30
I had almost the same issue on update to 9.10 except with Mythbuntu instead. Running sudo apt-get remove mythbuntu* fixed it and gave me the cool new 9.10 login theme. Thanks guys. :)

---

