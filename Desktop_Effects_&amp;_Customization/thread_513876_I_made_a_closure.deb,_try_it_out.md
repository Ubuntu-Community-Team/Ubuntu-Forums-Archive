---
title: "I made a closure.deb, try it out"
date: 2007-07-31
forum: Desktop Effects &amp; Customization
---

### Post by luckyd on 2007-07-31
Closure is an little application, that works very well with awn, its purpose is to be a graceful and stylish way to shutdown your system. I wanted to make it easier for everyone to install, so here is a .deb. Try it out and see if it works(it should) and if it doesn't please critique me. I am learning how to build .deb's.

---

### Post by Chilongola on 2007-07-31
downloads as a "php" file then my pc froze????????????????

---

### Post by Motoxrdude on 2007-07-31
Well, it half works. Nothing happens when i go "System>>Quit", just a normal logout screen (maybe that's now how the program is suppose to work?). When i goto the terminal and enter "closure" i get a black screen that goes opaque from the top-right to bottom-left, but nothing else happens.

---

### Post by Espreon on 2007-07-31
Yours is not needed, since Trevinho made one for both SVN and stable versions. But I am using Trevinho's and it most of the time partially works.

---

### Post by luckyd on 2007-07-31
Oh, i didnt know trevino had made one. :)

---

### Post by Ptero-4 on 2007-08-19
Closure kinda works. 
First: you need to run it from Applications > Other > Closure, not from System > Quit.
Second: you need to be using a composite manager to make it work fully.
Third: you will need to go to the gconf-editor to modify the commands it use. using sudo halt and sudo reboot is viable, but it breaks the usplash shutdown sequence and require modifications to the sudoers file.

---

