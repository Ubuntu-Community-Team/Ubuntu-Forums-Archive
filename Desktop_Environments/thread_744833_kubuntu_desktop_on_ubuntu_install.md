---
title: "kubuntu desktop on ubuntu install"
date: 2008-04-04
forum: Desktop Environments
---

### Post by dlbrando on 2008-04-04
A friend keeps telling me to switch to kubuntu because it works better, the problem is that I have already had to to a bit of tweaking on my laptop to get everything to work correctly(emachines n-10) if I just install the desktop will I get the advantages, or would i be better off uploading the entire setup again from scratch?

---

### Post by .nedberg on 2008-04-04
If the setup is for the computer (not user settings), they will be the same in Kubuntu. But your gnome settings will not work in kde (background, color theme, icons...). This can be configured though. Just install kubuntu-desktop and select kde when you log in.

---

### Post by warp99 on 2008-04-04
All of the flavors of Ubuntu (Ubuntu, Kubuntu, Xubuntu) are all the same except for the desktop. Ubuntu has Gnome, Kubuntu has KDE, and Xubuntu has Xfce, You can switch between each desktop or install all three if you like with the following commands:

```
sudo apt-get install kubuntu-desktop
sudo apt-get install xubuntu-desktop
sudo apt-get install ubuntu-desktop
```

Since you already have Ubuntu there is no need to run the last command. If you want to remove a desktop just replace install with the words 'remove --purge' and that will remove the desktop from your system. No need to re-install anything, this isn't Windows you know. ;)

---

### Post by wieman01 on 2008-04-04
Some things are different though and I assume that Ubuntu is slightly better. Bluetooth is a pain in Kubuntu, never got it work properly (command line workaround does the job though). Therefore I would install the Desktop on top of Gnome to begin with and see how it goes. Don't remove the current installation just yet.

I have been using Kubuntu and I'm very happy with it. But I had to do a lot of tweaking and research to get it up and running to my satisfaction.

I am happy to see other Kubuntu users here. :-)

---

### Post by dlbrando on 2008-04-04
so every time I log in it will give me te choice between desktop enviroments?  or every time I reset the desktop?

---

### Post by wieman01 on 2008-04-04
Yes, before you log in, you can choose between either desktop environment. The log-on screen (GDM) has such an option.

---

### Post by anjilslaire on 2008-04-04
There is an option on the logon screen (Sessions or similar) that you change to choose your Desktop. After that, it generally loads the last used choice, until you change it again.

That being said, I used to install Ubuntu, then load kubuntu-desktop ontop to make sure I had everything I needed. The last 2 installs however, (Feisty & Gutsy) I installed the OS from the Kubuntu ISO, and only add th gnome apps I need. 

Everything runs fine (although I dont use bluetooth, so I can't comment on that).

---

