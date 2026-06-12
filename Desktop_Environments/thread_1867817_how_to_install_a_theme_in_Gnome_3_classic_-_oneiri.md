---
title: "how to install a theme in Gnome 3 classic - oneiric"
date: 2011-10-23
forum: Desktop Environments
---

### Post by blackmail on 2011-10-23
So, I have installed on a laptop the Ubuntu 11.10 Oneiric distro. It works as a dream, all the drivers are there all the shortcuts and special keys are working perfectly, but it looks like an abomination. So i got rid of the unity thing, and then installed the Gnome classic interface. It is an upgrade, I also removed the actions option, and as the Ubuntu Classic desktop environment i tried to add back the places and applications menus, failing to have success with the system menu, which i understood later that will not be there and the options where scattered across Ubuntu's menus, that is not something i can't live without and also it is a bit refreshing, but i can't seem to figure out a normal way to install themes on this.

I don't want to sound like a noob, but I would like to ask for straightforward answers and very detailed ones.

What i did was enter to gnome-look.org, and downloaded some GTK3 themes. These i have unpacked and then copied them to /usr/.../themes but when i started the gnome tweaker it did not see the themes. They where unzipped...

Thank you in advance.

---

### Post by LarsKongo on 2011-10-23
First of all try to install it in *~/.themes* to see if that works.
If you don't have a .themes folder in your home folder you can create it.

Otherwise remove the theme(s) you installed in /usr/share/themes.
Then unzip the theme(s) to a temporary folder and type this in a terminal where the theme is located:
*chmod -R 777 name-of-the-theme*

Then try to copy it to /usr/share/themes and see if it works. I've noticed that Ubuntu users seems to have this problem with some of my themes. Strangely enough I never touch the permissions when I package my themes, and it seems to work just fine in other distributions.

---

### Post by Frogs Hair on 2011-10-23
For some reason I had to restart after I installed  my first theme and everything has worked since . As of today I have both Gnome and Unity running . There are some themes that have not been updated for Gnome 3.2 .

---

### Post by blackmail on 2011-10-24
Thank you both for the prompt replies, The chmod a=rwx and then creating the hidden themes folder in the home directory helped, the themes where loaded in the gnome tweak tool, but they did not show up properly. I hate the Unity desktop, i think it is horrible, and i don't think that it is linux anymore. It is supposed to make us htink before we do stuff, but stuff is missing from it, that must be installed on our own, after that we must also get used to the unity mentality which looks similar with the windows 8 thing. No sir, I am off from Ubuntu 11.10, I will slowly migrate to slackware. The whole Ubuntu comunity has offered so much to me and thank you, but the Gnome 3 implementation is deplorable, the nice functions and the support is due to the people over at kernel.org, where canonical fails to provide some help, and also seems like Ubuntu is getting more and more windows like. I think i will mess around with it and change back the desktop to gnome 2 ubuntu 10.10 style, and let you know if i will have success also i will try to make it al as simple as downloading a .sh script. Bye till then.

---

