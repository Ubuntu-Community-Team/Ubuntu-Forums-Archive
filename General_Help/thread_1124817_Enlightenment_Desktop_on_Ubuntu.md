---
title: "Enlightenment Desktop on Ubuntu?"
date: 2009-04-13
forum: General Help
---

### Post by IHeartMyiBook on 2009-04-13
Can you install Enlightenment onto Ubuntu? I have seen some screen pics and it looks really cool so i wanted to see if i could install it in like you can with Xfce or KDE ^_^

---

### Post by skymera on 2009-04-13
I think you're able to, but i have absolutely no idea how.

afaik gOS uses Englightenment, let me double check. No it seems it used Gnome now but it's based on Ubuntu.

I tried Enlightenment with gOS few years ago. Took a lot of configuring but it ended up looking smashing.

Hope someone else can help  :)

---

### Post by freakyzoidberg on 2009-04-13
afaik e16 is in the repository.

for e17 you have to compile it from svn, the is a know deb who do it for you.

> sudo sh -c "echo 'deb [http://cafelinux.org/Downloads/oz-os](http://cafelinux.org/Downloads/oz-os) tinwoodman main' >> /etc/apt/sources.list
wget -q [http://cafelinux.org/Downloads/oz-os/key.asc](http://cafelinux.org/Downloads/oz-os/key.asc) -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install cvs
sudo apt-get install e17-svn

and done :)

---

### Post by IHeartMyiBook on 2009-04-13
Thx! i will try it once the official Jaunty comes out >.< my wireless just died so i am going to wait as the driver i need will be included in jaunty so i won't have to add drivers in for my wireless card to work ^_^

---

