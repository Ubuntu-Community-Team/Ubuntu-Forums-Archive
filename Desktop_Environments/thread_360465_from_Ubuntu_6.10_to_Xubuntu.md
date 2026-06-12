---
title: "from Ubuntu 6.10 to Xubuntu"
date: 2007-02-13
forum: Desktop Environments
---

### Post by lanchongzi on 2007-02-13
hi there

i ran  Xubuntu on my PC but it was hard to install stuff - for me that is ( Computer idiot, that I am )

so I decided to install Ubuntu 6.10 over it
which is VERY SLOW 
so my question now is: can i go from Ubuntu 6.10 to Xubuntu
and   do I get to keep whatever  installed before?
and how to do it?



every help is appreciated 


lanchongzi

---

### Post by Titus A Duxass on 2007-02-13
You can do what you want (nearly) with Ubuntu.

sudo apt-get install xubuntu-desktop will get you your desired Xubuntu.
sudo apt-get remove gnome-desktop will remove you slow gnome.

If you lose any packages just apt-get install them back.

---

### Post by lanchongzi on 2007-02-13
so, now i did the first step

before i do the second : sudo apt-get remove gnome-desktop

i kinda wanna ask, canI also go back to Ubuntu, for the case i decide to do so?


and another question.
if i dont do the second input, can i choose between the two?
and how


thank you  a lot

---

### Post by Richard Kut on 2007-02-13
Hello lanchongzi. When you installed Xubuntu and Ubuntu, they both created entries in the session menu of the login screen. This means that you can have both installed on your machine, and can select which one you want to use when you login.

To access the session menu when you are logging in, and before you enter your password and hit Enter, press the F10 key. This will bring up a small menu. Select the Sessions... option, and then select either Xubuntu or Gnome (or KDE or any other window manager that you might have installed). Then hit Enter to login to your choice!

---

### Post by lanchongzi on 2007-02-13
Thanks a lot

this is really sweet!!!

Now i have both,  thats WAY better then reading 1001 posts/threads about which desktop environment is better and why.

thanks Richard.

---

