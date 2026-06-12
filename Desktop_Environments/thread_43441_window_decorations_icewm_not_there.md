---
title: "window decorations icewm not there"
date: 2005-06-22
forum: Desktop Environments
---

### Post by usergentoo on 2005-06-22
What happen to icewm in the "window decorations"section of the control center. I dont see it there. In older versions of KDE Ive seen it. 

How do I get it back?

---

### Post by Zeddicus on 2005-06-22
[QUOTE=usergentoo]I dont see it there. In older versions of KDE Ive seen it. 
[/QUOTE]

What version of KDE are you using?  It shows up fine here (3.4.1).

---

### Post by usergentoo on 2005-06-22
Using 3.4.0
I did the install from the cd after I installed Ubuntu.
I just looked thru the package manger and seen kde for 5:42ubuntu1 would this be a wise thing to do and install this?

---

### Post by Zeddicus on 2005-06-22
I'd suggest updating your packages that can be updated if that's what you're asking, yes. :)

sudo apt-get update && sudo apt-get dist-upgrade would do nicely.

---

### Post by usergentoo on 2005-06-22
tried that it didnt update anything

looked at the package manager and it dosent show kde as being an update either

---

### Post by usergentoo on 2005-06-22
Ok I used the package manager to install kde 3.4.1 now I have multiple versions of kde and there not getting along.

Heres how I installed . First I installed Ubuntu Hoary then decieded to install KDE on top of that so I used the Kubuntu cd to install it. This installed KDE 3.4.0 and I then updated all packages. It didnt do anyupdates for KDE. So I used the package manager to install KDE 3.4.1 now I have mutliple versions of KDE. 

KDE 3.4.0 was not listed as a installed item in the package manager.So I asume that since it didnt show up when I installed 3.4.1 it didnt know I already had KDE installed, maybe thats why it installed a seperate version.Maybe thats also why it didnt show KDE 3.4.1 as being an updated version. 

Im kinda clueless?  I dont know to much about Ubuntu yet still new to it, Ive used Gentoo since around 2001.
So you can uderstand my frustration of trying to use a new distro. 
Im really not sure what to do from here or where to go.

---

### Post by usergentoo on 2005-09-06
I have upgraded to version of KDE 3.4.2
I still dont see the icewm themes heres a screen shot of what shows up.

 [IMG][IMG]http://i22.photobucket.com/albums/b311/killerklown28/snapshot2.png[/IMG][/IMG]

---

### Post by f1dave on 2005-09-07
Try this in the console:

sudo apt-get install kdeartwork-theme-window

See if that delivers the goods.

---

### Post by usergentoo on 2005-09-07
I tried it didnt help.
I went ahead and installed Mepis and it does have it in the menu.
Ive also notice there are alot of things missing between Mepis and Kubuntu.
Why sre there alot of items missing in KDE?  Several menu items are not found in the Kmenu either. I had to add manualy add these. Why is Kubuntu like this. I have the same version of KDE for both distro's and just dont understand.


This is somewhat a dissapointment. Im gona keep Kubuntu on my laptop. But on my desktop I think Ill stay with Mepis and see how things go.

I do appreciate the help.

---

### Post by f1dave on 2005-09-07
Had you added the backports and universe repos as described at ubuntuguide.org? That makes available a lot of the "missing" packages you talk about.

---

### Post by usergentoo on 2005-09-07
I did have all the backports aded.
Its funny cause this is the only distro Ive seen to act like this.
I teach children and adults to use linux at the local schools and they have gentoo installed on them and they dont have any of the oddball problems found here.Its just odd.

---

### Post by f1dave on 2005-09-07
ubuntu is fairly new. Even so, i dont understand your problem not working- i have all of those windecs, as do others who have posted.

gentoo's emerge is awesome, interesting you're teaching kids that tho as its not atypical of linux package management and upgrading. good on ya.

---

### Post by usergentoo on 2005-09-07
I dont have a real job Ive been currently laid off from the local nuclear power plant, and now just devote my time to volunteer teaching.Basicly  just showing how to navigate around in linux and showing the differences between windows and linux.It really isnt the greatest feeling in the world when you dont have a job and trying to support your wife and son on unemployment.

---

