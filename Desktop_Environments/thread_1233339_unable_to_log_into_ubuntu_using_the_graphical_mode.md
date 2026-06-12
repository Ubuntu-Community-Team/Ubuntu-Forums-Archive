---
title: "unable to log into ubuntu using the graphical mode"
date: 2009-08-06
forum: Desktop Environments
---

### Post by abelito8 on 2009-08-06
Good evening, 

I have kubuntu 9.04 installed in my computer and I am normally using a Gnome environment desktop (though I get back to KDE or Xfce if I have any troubles with Gnome) 

This afternoon I restarted my computer and since ever I am unable to log in. I press the on button, get to the partition page and select Ubuntu 9.04 and the computer shows the login page

however, once I type in my password, the computer tries to log in but then brings me back to the login page asking for the password again. I have tried to login as Xfce, Gnome, KDE, Failsafe mode and the result is the same. The only way to get through is to login through the terminal, but then I am unable to get back to the graphical mode. Any help?

---

### Post by cajunlibra on 2009-09-23
I'm having a similar issue as well.  If i try to use the previous kernel, i get a list of errors that looks like coordinates having to do with USB.

---

### Post by cajunlibra on 2009-09-24
I had forgotten that I have encountered this issue before.

I remembered the solution. In my case, there wasn't enough free HD space for the desktop managers to run.

I had installed XP under virtualbox which left me with little space. When I did df -h, my root partition showed 100% was used.

To solve, I logged into the Console(Terminal) and removed the file associated with XP and restarted the computer with no problem.


See if this works for you.

---

### Post by abelito8 on 2010-01-29
Yes I have also 100 used....
and I also have some windows installed (I was too lazy to delete it so far, I had formatted it but it did not really work)

but what are the commands to find the windows part and how to delete them?

---

### Post by Zorael on 2010-01-29
As for clearing space, if you boot up into recovery mode (for which there should be entries in your GRUB menu), you'll be greeted with a menu which includes a 'free space' option. It will delete the apt cache; basically, archives (.debs) of downloaded apps and libraries (including updates of them). 

Pick it and then 'reboot'.

('resume' is also an option, but I find it just leaves me at a terminal instead of starting the graphical environment.)

---

