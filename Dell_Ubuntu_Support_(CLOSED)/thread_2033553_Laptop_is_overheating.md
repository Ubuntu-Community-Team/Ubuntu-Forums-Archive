---
title: "Laptop is overheating"
date: 2012-07-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ruza on 2012-07-26
Hey all, 

I've got some problems using ubuntu. I own a Dell n7110n laptop. While using Ubuntu, or any linux at all my computer is overheating. Laptop fan is working all the time. Computer is not dirty or something like that. 

Some clues that can help:
- Im using bumblebee
- Battery lifetime is 2 or 3 times shorter compared when using Windows - so i guess something is working in background that keeps my laptop hot and fan working
- im using kernel 3.2.0-27

---

### Post by miguelpires on 2012-07-26
> **ruza said:**
> Hey all, 

I've got some problems using ubuntu. I own a Dell n7110n laptop. While using Ubuntu, or any linux at all my computer is overheating. Laptop fan is working all the time. Computer is not dirty or something like that. 

Some clues that can help:
- Im using bumblebee
- Battery lifetime is 2 or 3 times shorter compared when using Windows - so i guess something is working in background that keeps my laptop hot and fan working
- im using kernel 3.2.0-27

Hi,
Have you try Jupiter? Sove my problems in my Toshiba laptop and in my Alienware.
Regard's
Miguel

---

### Post by ruza on 2012-07-26
nope... i don't even know what is Jupiter... I will check it out. Thanks

---

### Post by miguelpires on 2012-07-26
> **ruza said:**
> nope... i don't even know what is Jupiter... I will check it out. Thanks
try this link [http://www.webupd8.org/2012/03/jupiter-applet-officially-switches-to.html](http://www.webupd8.org/2012/03/jupiter-applet-officially-switches-to.html)
regards
Miguel

---

### Post by ruza on 2012-07-26
Ok, i think that Jupiter is solving the problem cheers mate! :) Thanks

---

### Post by ruza on 2012-07-27
Sorry for double post. I have found the reason for overheating, so this thread is not solved. Seems that, at some point xfapplet in xfce panel goes fully retard and takes 100% of cpu time. After killing them everything went back to normal. 

Interesting thing is that I noticed 2 xfapplet processes and I am using only one applet. Problem happened after several logout/logins so i guess that - either something started the process or it forked itself. I found a couple year old bug, but developers said that the fix is to be released in  Lycid. 

[https://bugs.launchpad.net/ubuntu/+source/xfce4-xfapplet-plugin/+bug/323909](https://bugs.launchpad.net/ubuntu/+source/xfce4-xfapplet-plugin/+bug/323909)

Does anyone know how to solve that?

---

