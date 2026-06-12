---
title: "Xfburn or Nautilus ?"
date: 2006-11-10
forum: Desktop Environments
---

### Post by rfruth on 2006-11-10
What do Xubuntu (or other) users prefer for burning CDRWs, Xfburn or Nautilus, something else ?

---

### Post by emgy on 2006-11-12
I have installed Xubuntu 2 days ago on a Compaq Evo N1020v laptop. It runs very well and I am generally impressed. One major problem: Xfburn will not burn an ISO file to CD. It just claims "Operation finished" when nothing has actually happened.
Nautilus will install and start, but on closing, desktop turns Ubuntu brown and right click looses functionality. 
I installed K3b but it does not work at all.
I installed Xubuntu on my son's desktop PC and got exactly the same problems.
However, both machines happily burn ISO's using K3b when Ubuntu is installed.

So, in answer to your question, there does not seem to be a usable burning program with Xubuntu.

---

### Post by Qew on 2006-11-13
I have Xubuntu Dapper and can get K3b to work fine with it. There's also Gcombust that works (it's not pretty, but it does do the job fine). I know that K3b is a KDE application and that I have to install a few KDE libraries to get it running, but it's the best burning application for Linux right now, so it'd be silly to cut off one's nose to spite one's face.

---

### Post by dannyboy79 on 2006-11-13
what about just using the command line, it's a really easy command to run. to make an iso you use growisofs to burn it the same, check it out here: [http://www.linuxcommand.org/man_pages/growisofs1.html](http://www.linuxcommand.org/man_pages/growisofs1.html)
i believe it's part of the latest dvd+rw-tools which the latest you can get from here [http://fy.chalmers.se/~appro/linux/DVD+RW/tools/?M=D](http://fy.chalmers.se/~appro/linux/DVD+RW/tools/?M=D) 
since the one apt-get gets isn't the latest.

---

### Post by Kindred on 2006-11-13
Graveman works for me.

edit: though I believe it has problems burning ISO to DVDs.

---

### Post by rfruth on 2006-11-13
I currently use Nautilus but this is food for thought, thanks !

---

### Post by emgy on 2006-11-16
I fixed K3b on Xubuntu.
Select Settings - K3b Setup, then in the Devices section, it says check the devices whose permissions you want to be changed. I put a tick in the box by the entry for my cd writer, and K3b now works fine. Some sort of permissions issue apparently. I think it has given the cd writer root permission.

---

### Post by 3rdalbum on 2006-11-16
Under XFCE, if you perform the command "killall nautilus", that should restore your desktop.

---

