---
title: "Launch applications from terminal / putty"
date: 2008-12-11
forum: General Help
---

### Post by pandaking on 2008-12-11
Hi,

Really nooby question here, but how can I launch an application from terminal / putty?

The program is already installed, it just needs launching. At the moment I have to use my NX client (NoMachine) to remotely connect to the computer, and then run the program from the menus.

I am sure there must be an easier way.

I have tried right clicking the icons, clicked "make link" and copied those links to my home folder. My thinking was then when I connect with putty, I could just type the name of these shortcuts (or links) and they would run. As I am sure you will realise this didn't work :p

I have searched around for answers, and from all the guides I have read I can now navigate around the terminal like no man, but I still haven't found an answer to launching an application.

Many thanks...

---

### Post by Titan8990 on 2008-12-11
If you are referring to a GUI program then no. Keep in mind however that nearly all Linux GUI programs are just front-ends for command line programs.

---

### Post by ibutho on 2008-12-11
If you are running ssh on a Linux machine, you can use X forwarding to run GUI applications from a remote machine. I don't think this will work with putty on Windows because you need to be running an X server.

---

