---
title: "Netgear WG311v3 on Kubuntu"
date: 2008-04-20
forum: Desktop Environments
---

### Post by BlackLight94 on 2008-04-20
Let me say first that this as far as I can tell a Desktop Environment problem, because I have the same files working fine on my Ubuntu Gutsy Gibbon Live CD (that's what I'm using to post this). So anyways I have the ndiswrapper files(the common and the utils) and they are in .deb format, and the problem is that I'm trying to use the Kubuntu 8.04 rc KDE4 remix, and there is no option to install it in dolphin, I tried it in command line too, and if i do that there is a line of errors.

---

### Post by benerivo on 2008-04-21
Ubuntu uses a program called gdebi to install .deb packages. The kde front end is called gdebi-kde and you may need to install this program, and maybe set .deb files to automatically open with it from dolphin. What did you try from the command line?

I would firstly install the gdebi stuff with ```
sudo apt-get install gdebi-core gdebi-kde
```then try right clicking a .deb file and setting it to open with gdebi-kde. If this fails then try typing ```
sudo gdebi
```in a terminal, then a space, then drag the .deb file in to the terminal and choose paste. Then hit return. If this gives errors, then post them here and someone may be able to help further.

---

### Post by BlackLight94 on 2008-04-24
I would try to apt-get, but the problem is that the packages that I'm trying to install are the packages for my WiFi, and I have no Wired connection.

---

