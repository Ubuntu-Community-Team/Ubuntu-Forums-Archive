---
title: "Installing .deb's"
date: 2005-12-06
forum: Desktop Environments
---

### Post by linnuxx on 2005-12-06
I run brezzy on my computer, and i don't have internet on that computer, but i do have internet on a differnt computer that runs WinXP and i want to put more   programs on the linux one.
How do i install the programs localy on the linux system? :???: 
I can download the debs, but i have no clue on how to install the programs.

Thanks :)

---

### Post by aysiu on 2005-12-06
If it's on your desktop...
```
cd Desktop
sudo dpkg -i nameofprogram.deb
```

---

### Post by cstudent on 2005-12-06
You can install a deb file using the command "**dpkg -i *package_name***". However, you should be careful. You would want to use Ubuntu debs from an ubuntu repository. Other deb files may or may not work. You can learn more by enter "**man dpkg**" in a terminal window. You'll probably also run into dependecy problems.

You could also use your windows machine to share internet connection with your linux machine. Each machine would need an ethernet card, which may already be present. I would use a network switch to connect the two machines together. They're not too awfully expensive these days. Just cable the two machines together with the switch in the middle. I'm assuming you're on dialup, so turn on internet connection sharing on XP and use the network wizard in XP to setup the network. It should work. I've done it myself in the past.

---

