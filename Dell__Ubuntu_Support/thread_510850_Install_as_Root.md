---
title: "Install as Root"
date: 2007-07-27
forum: Dell  Ubuntu Support
---

### Post by jagger27 on 2007-07-27
I am stupid and I need to install the file: NVIDIA-Linux-x86_64-100.14.11-pkg2.run. But it won't let me install! It says I need to be root or something. Please help, Windows is so blah, I like Linux! 

I JUST NEED THIS DRIVER!!!!!

---

### Post by rombel4u on 2007-07-27
open a terminal ( Application-->Accessories-->terminal)

then type: sudo and the rest of the command you use before.

---

### Post by pbcartwright on 2007-07-27
from the command line:
sudo chmod 777 NVIDIA-Linux-x86_64-100.14.11-pkg2.run.

then:
sudo ./NVIDIA-Linux-x86_64-100.14.11-pkg2.run.

the first command makes it executable, the second command installs it.

---

### Post by shredsalot on 2007-07-27
And... to su root, you need a password.  Evidently, it's not the first user's password either.  But, you can go into the user manager and set it to whatever you want though.

The next problem you are going to run into is that the installer will fail and ask you to exit xwindows before you run it.  Windows installers will be nice enough to add a small batch file to the dos mode part of your boot sequence, but linux/ubuntu driver insallation does no such thing.

I have yet to figure out how to get into a windowless console mode on my ubuntu box to do this next step.  If you figure it out, let me know.

---

### Post by bluenova on 2007-07-27
> **shredsalot said:**
> 
I have yet to figure out how to get into a windowless console mode on my ubuntu box to do this next step.  If you figure it out, let me know.

sudo init 3

And to get back to graphical mode:

sudo init 5

---

### Post by shredsalot on 2007-07-27
sudo init 3 does absolutely nothing in terminal.  ???

---

### Post by jordan86 on 2007-07-28
hmm..
if not mistaken, you need to log in as root.
Go to terminal and type su
after that, you need to key in your root password, not user password.
If you haven set your root password, then you type sudo passwd before type su log in as root.

---

