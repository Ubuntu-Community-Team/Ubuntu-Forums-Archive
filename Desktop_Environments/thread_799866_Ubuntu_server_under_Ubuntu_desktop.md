---
title: "Ubuntu server under Ubuntu desktop ?"
date: 2008-05-19
forum: Desktop Environments
---

### Post by killersoft on 2008-05-19
Hi all 
I am a new user in a unix systems, but i very like ubuntu and i want to learn everything about it. 
I have installed Ubuntu Desktop 8.04 i386  on my computer 
and 
Ubuntu server 8.04 
IS there a way to Run My Ubuntu server when i using my ubuntu desktop 
just will be more easy for me to read in internet and make changes on my server. 
If you know some other way please tell me!
I will be very glade. 

*I don't have very good english but i am trying*!

---

### Post by .nedberg on 2008-05-19
If you have them installed as separate OS'es and coose at boot, then there is no way to do this. But everything your server can do, your desktop can do too!

In a command line do 'sudo tasksel' and you will get the option to install some server applications.

---

### Post by killersoft on 2008-05-19
if you know other way tell me

---

### Post by killersoft on 2008-05-19
Now i am using Ubuntu Desktop and i have Virtual mshine manager can i boot my ubuntu server ?
And which file exactly to boot

---

### Post by killersoft on 2008-05-19
I just want to host my web sites on my computer 
but ubuntu server is very difficult for me ?
Is ubuntu desktop slower than ubuntu server
My pc is 1000 ram ddr 400 procesor amd sempron 2200 1.5ghz 
Is he enough for a LAMP server for a small websites ?

---

### Post by .nedberg on 2008-05-19
You can run a Ubuntu server inside a Virtual Machine, no problem!

That machine should have no problem running the the desktop version of Ubuntu with a LAMP server inside a Virtual Machine.

---

### Post by killersoft on 2008-05-19
Tell me which way is better i want to be whit ubuntu desktop.
And 
which will be more faster to boot ubuntu server in virtual machine or 
just to run LAMP in my ubuntu desktop

---

### Post by .nedberg on 2008-05-19
I would not run a LAMP server on my desktop, but is no problem to do it.

Running the server on the desktop would be faster than in a VM.

If you go the VM way you have the added benefit of being able to use snapshots. Messing up a server is easy the first time, and with snapshots it is easy to revert to a previous state.

Both methods have benefits and disadvantages, you have to make the choice yourself.

---

