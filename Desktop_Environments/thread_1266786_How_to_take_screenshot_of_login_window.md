---
title: "How to take screenshot of login window?"
date: 2009-09-15
forum: Desktop Environments
---

### Post by futureal2032 on 2009-09-15
Hey i want to know how to take and save screenshots of the Ubuntu login screen?

is there any specific program or keyboard shortcuts?

i have seen people post screenshots of their startup process..ubuntu splashscreens at startup and login window..i want to know how i can do that.

:)

---

### Post by lyni on 2009-09-15
try the "Print Screen SysRq" key. it is to the right of the Backspace key on the keyboard.
good luck with it.

---

### Post by yabbadabbadont on 2009-09-15
gdmthemetester or Xnest for the login screen.

Bootup sequence is probably being captured by booting inside of a virtual machine like Virtualbox or VMWare.

---

### Post by aysiu on 2009-09-15
> **futureal2032 said:**
> Hey i want to know how to take and save screenshots of the Ubuntu login screen?

is there any specific program or keyboard shortcuts?

i have seen people post screenshots of their startup process..ubuntu splashscreens at startup and login window..i want to know how i can do that.

:) The splash screen... easiest way is probably to run Ubuntu inside of VirtualBox. More details here (uses VirtualBox inside Windows as an example, but the same applies to VB inside Linux or Mac OS X):
[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

If you want a quick screenshot of the login window, though, just paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo apt-get update
sudo apt-get install xnest
gnome-screenshot --delay 10 &
gdmflexiserver --xnest
```

---

### Post by Possum Films on 2009-09-15
Just install Xnest with Synaptic package manager and then use Applications > System Tools > New Login in a Window. Once you have done that all you need to do is press the Print Screen key (located between F12 and Scroll Lock) and that should take a screenshot. 

I've attached a picture of what it should look like (please note that in the screenshot I changed the login window theme so yours probably won't look the same).

---

