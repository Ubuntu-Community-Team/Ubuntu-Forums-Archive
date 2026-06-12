---
title: "Virtual Box share"
date: 2007-08-28
forum: Desktop Environments
---

### Post by tajreed on 2007-08-28
Can't seem to get "share" working with Virtual Box with XP as the guest. After installing VB extras, I use the following at the C: net use X: \\vboxsvr\ home/duke/winxp(this being the path to the shared folder labeled "winxp".
I get error 53. 
I must be typing a wrong command at the C: Can anyone give me the exact format for doing so?

---

### Post by raja on 2007-08-28
Nope.
You have to create the share first with the path to the shared folder.
Then within windows when you issue the net use command, you only give the name of the share that you have already assigned.
Check the manual or [here]("http://reachbeyondgrasp.blogspot.com/2007/04/how-to-install-virtualbox-in-ubuntu.html") for details.

---

### Post by tajreed on 2007-08-29
Hey, thanks. That did it.

I really appreciate your efforts.

JR

---

### Post by lfvsouza on 2007-09-04
Hey Raja !!

 Excelente suggestion ! That did it for me too !! Now I DONT have a good enough reason to dual boot microsoft !!! long live UBUNTU !!
 Tanx all !

---

