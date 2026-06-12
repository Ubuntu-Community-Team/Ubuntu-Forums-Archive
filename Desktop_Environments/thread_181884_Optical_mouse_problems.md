---
title: "Optical mouse problems"
date: 2006-05-24
forum: Desktop Environments
---

### Post by Darvos Omcon on 2006-05-24
The mouse is a Micro Innovations Ps/2 optical mouse with scroll wheel.
Once gnome loads, the cursor stays in the middle of the screen and doesn't move. When you click the mouse, it goes to the top right corner and it responds to clicks. Please help.

---

### Post by K.Mandla on 2006-05-24
This might be dumb, but I've had problems that sounded like that, and it turned out I had the mouse plugged into the keyboard socket. Any chance that's the case ... ? :rolleyes:

---

### Post by Darvos Omcon on 2006-05-24
Nope, the keyboard's in and working fine. :)

---

### Post by Mustard on 2006-05-25
Can you paste the contents of your xorg.conf?  I'm not sure how you are going to do that without a mouse, but it would be helpful to see it.

When you run sudo dpkg-reconfigure xserver-xorg what option do you choose for the mouse?

---

### Post by Sef on 2006-05-25
Since you have two computers, could you plug the other computer's mouse in and see if it works.

---

### Post by Darvos Omcon on 2006-05-25
The other mouse has the same problem. I tried the live CD for 5.10 on this machine. Same thing. Freezes in the top corner.
Mustard, I dont know how to show my xorg.conf. Im new to Linux, and IM just getting acquainted with all the commands. I can get to the text login by pressing Ctrl+Alt+F1, but how do I get to the xorg.conf file? When I do the dpkg-reconfigure xserver-xorg, I don't emulate a 3 button mouse, and I enable scroll events, other than that, Im lost.

---

### Post by Ramses de Norre on 2006-05-25
```
less /etc/X11/xorg.conf
```

But I doubt you'll find anything in there..

---

### Post by Darvos Omcon on 2006-05-25
Thanks for all your help, guys. I went and got a USB optical mouse. It works like charm. I appreciate all your help, though. :-D

---

### Post by Mustard on 2006-05-25
[QUOTE=Darvos Omcon]Thanks for all your help, guys. I went and got a USB optical mouse. It works like charm. I appreciate all your help, though. :-D[/QUOTE]

Well thats a good method of fixing it. :D

Glad you got it working.

---

