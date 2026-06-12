---
title: "kubuntu desktop not appearing."
date: 2009-05-19
forum: General Help
---

### Post by shejohn on 2009-05-19
Hey,
I'm new to Kubuntu and linux.
I have installed Kubuntu 9.04.. After purging Synaptic i'm not able to get Kubuntu desktop back.
I tried alt+cntrl+f2 and tried sudo apt-get install kubuntu-desktop but the desktop still doesnt come.
All i can do is just log in and see my pointer and use the alt+cntrl+f keys and del key.
Pls help!

---

### Post by KhurramM on 2009-05-19
Use

sudo apt-get --fix-missing

Maybe it helps.

Try fix in the recovery mode.

If u r just wasting time, here and there,

try a reinstalling ubuntu all over. It takes only 30 minutes.

adios

---

### Post by shejohn on 2009-05-19
Hey, problem resolved!

I used the suggested command
 sudo agt-get --fix-missing 
but the command line option was not getting accepted.

I tried sudo apt-get install kubuntu-desktop and i got my desktop back!

Thanks!

---

