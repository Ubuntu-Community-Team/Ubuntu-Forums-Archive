---
title: "Run a program on a remote server"
date: 2009-03-09
forum: General Help
---

### Post by stim on 2009-03-09
Hello,
  I am running a ssh/web server on my home box, as well as sharing my music with simplifymedia.   Sometimes, I forget to start simplifymedia before leaving for work.  I would like to be able to ssh into my home box from my work box and run simplifymedia.

In case you don't know what simplifymedia is or how it works, it is a simple file sharing application that allows you to stream your music over itunes/winamp/rythmbox.  All you do for linux is run simplifymedia on both computers and your music is available. 

In this case, I either have a)forgot to run it or b) it has crashed, and I need to restart it.  SSHing in and running ./SimplifyMedia results in the SimplifyMedia executable being invoked in my current machine (work laptop) when I want it invoked on the remote machine (home desktop).  

Any ideas?

---

### Post by Aenima99x on 2009-03-09
After you SSH in, enter ```
DISPLAY=:0 ./Simplifymedia
```
See if that works for you.

---

### Post by kanikilu on 2009-03-09
I spend a lot of time logged into my servers through SSH and I've never encountered a situation where running a command in a remote session results in a local program being run :?:

Maybe trying logging in to the remote computer with ssh -X to forward X11?

---

### Post by stim on 2009-03-09
Aenima,that was exactly what I needed. Thank you. 

I think the problem was that I was ssh'd in with X enabled (ssh -YC) , and it was forwarding the gui to my work box, when I wanted the whole shebang run on the remote box.

---

### Post by Aenima99x on 2009-03-09
Cool glad it worked for you.

---

