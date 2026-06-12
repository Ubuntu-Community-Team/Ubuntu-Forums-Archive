---
title: "error updating to 686 kernel"
date: 2006-01-02
forum: Desktop Environments
---

### Post by jubuntu on 2006-01-02
tried updating 686 kernal with this line

> sudo apt-get install linux-686

and got this in reply
> 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

as a complete noob ive got no idea what this means.  can anyone point me in the right direction?

thanks.

---

### Post by mazelado on 2006-01-02
It looks like you cancelled a package installation during a previous install. dpkg keeps track of which packages have been installed and which haven't finished installing. It sees a half-installed package and wants to finish, giving you the error message you see. Try running the 'dpkg --configure -a' command. It will attempt to finish the installation of whichever packages were canceled.

---

### Post by jubuntu on 2006-01-02
whats the exact text line i need to enter in the terminal screen?  i cant get it to do anything.  thanks for any help you can give.

---

### Post by jubuntu on 2006-01-02
never mind, used the gui installer and found success.

---

### Post by Lord Illidan on 2006-01-03
Good for you, jubuntu... There was no need to PM me though...just post another thread.

---

