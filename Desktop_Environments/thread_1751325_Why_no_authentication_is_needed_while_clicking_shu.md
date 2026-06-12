---
title: "Why no authentication is needed while clicking shut down button?"
date: 2011-05-06
forum: Desktop Environments
---

### Post by sahiljha84 on 2011-05-06
Hey All,

When you want to shutdown the system from terminal we type 

sylar@ubuntu:~$ init 0
init: Need to be root
sylar@ubuntu:~$ sudo init 0
[sudo] password for sylar:

So it asks for a root password to shut down the system.

While when we click Shutdown button from the menu..it does not asks for a password, even though I not Root and I am able to shut down the system easily.

Anyone knows Why ?

---

### Post by Frogs Hair on 2011-05-06
It could be , so users without sudo permissions can shutdown the computer. Though I have not done it , it is probably possible to set up a password requirement for shut down .

---

### Post by 3Miro on 2011-05-06
Because clicking on the menu doesn't invoke the "shutdown" or "halt" commands directly. It goes through a program called PolicyKit, which determines who and how can do what. There should be a way to interact with PolicyKit from the terminal, although it is mostly used at the level of the Desktop Environment.

Google tutorials on PolicyKit for more details.

---

