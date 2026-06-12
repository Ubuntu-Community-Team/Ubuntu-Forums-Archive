---
title: "2 ? dual pros and source list"
date: 2006-04-16
forum: Desktop Environments
---

### Post by kc8pdr on 2006-04-16
I have a dual pros. computer . I would like to know how I can know if there both bing used ? And if not how to get it to work . The 2 ? is how do I add some source to the source list I want to install freevo ?

---

### Post by ubernoob on 2006-04-16
You need to install the SMP kernel to enable both your processors. Application --> System Tools --> System Monitor should show two graphs. One for each processor.

uname -a tells you which kernel you have installed. Find a similar with SMP.

Go to [http://freevo.sourceforge.net/cgi-bin/doc/FreevoAptUbuntu](http://freevo.sourceforge.net/cgi-bin/doc/FreevoAptUbuntu)
for installation instructions. 
sudo gedit /etc/apt/sources.list
for installing the 3 first lines in the source list.

---

### Post by gingermark on 2006-04-16
[QUOTE=ubernoob]sudo gedit /etc/apt/sources.list
for installing the 3 first lines in the source list.[/QUOTE]
As this is the Kubuntu forum, I'm gonna assume the OP is using Kubuntu.
So, 'kdesu kate /etc/apt/sources.list'.

---

### Post by ubernoob on 2006-04-16
Sorry.... you are totally right!! I was searching unanswered posts and didn't check which forum it was posted on. Thanks for correcting me.:oops:

---

