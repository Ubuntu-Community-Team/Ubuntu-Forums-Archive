---
title: "I'm trying to put a desktop GUI on a server build"
date: 2007-05-31
forum: Desktop Environments
---

### Post by thomas.clarke on 2007-05-31
Hi all,

I'm completely new to Linux so I hope I'm not making a fool of myself by asking this...

Is there a reasonable way of putting the desktop GUI on a server installation of Ubuntu 6?
And if so, to what extent would it represent the specific server capabilities (not much I presume).

Thanks

Tom

My setup:

dual 450MHz Pentium II server
4GB Raid 
DVD RW

---

### Post by ikonia on 2007-05-31
1.) why would you put a gui on a server - just use the desktop version
2.) what server capabilities are you refering to ?

---

### Post by llamakc on 2007-05-31
sudo apt-get install ubuntu-desktop (for Gnome)

sudo apt-get install kubuntu-desktop (for KDE)

sudo apt-get install xubuntu-desktop (for XFCE)

---

### Post by thomas.clarke on 2007-06-01
Hi,

Thanks for your responses guys.
In answer to the questions in the first response.

1) Coming from years of using Windows I was a bit startled by being presented with a command line and not having a clue what to do with it. I was hoping a GUI could show me around, so to speek. 

2) I don't know. After years of persuasion I've finally gained an interest in learning Linux. As I'm trying to learn the networking aspects of the system (that's the only reason I installed the server version, not because I know of the difining features), if the GUI is hiding something important I should learn I'd like to know.

To the second response, 
Thanks for the info I'll look into it.

Tom

---

### Post by pbw on 2007-06-01
Try installing something like webmin and phpmyadmin rather than a gui desktop if you'd like some gui tools for certain tasks. If you'd really like a gui however, i'd say to install a light wm. A full blown desktop on a server setup is a waste of resources.

-- pbw

---

### Post by reckless2k2 on 2007-06-01
yeah....stay away from the desktop bloat versions especially if this is a server box with limited hardware. install webmin as suggested in the above post and you can log into the box via browser from another box to admin it. webmin is very good.

---

### Post by bmartin on 2007-06-01
For a light window manager, I recommend Fluxbox. I've tried a lot of WMs and it gives you the most bang for your buck. It shouldn't slow down your computer much while running and has a very light footprint. It's ***very basic*** and very fast. If you decide to use it, PM me and I can give you suggestions on setting it up.

---

