---
title: "need help to install packages"
date: 2005-11-15
forum: Desktop Environments
---

### Post by bullfrog on 2005-11-15
how do i install packages if they are on desktop?also in add and applications it says the one there is installed. but i havent found on desktop any where. please give me step by step inst. on how to do it. i have looked almost every where but havent found answer.thanks alot for your help as i am new to ubuntu.  bullfrog:confused:

---

### Post by manicka on 2005-11-15
Do you mean that you have downloaded a deb package to the desktop and want to install it?

If so, in a terminal do the following 

```
cd Desktop
sudo dpkg -i *packagename*.deb
```

---

### Post by aysiu on 2005-11-15
I'd start off by reading [this](http://www.psychocats.net/linux/installingsoftware.php) for ways to install software in Ubuntu.

However, if Add Applications says it's already installed, it's probably already installed. What program are you trying to run?

---

### Post by Samuel on 2005-11-15
[HERE]("http://www.psychocats.net/essays/winuxinstall.php") is a good guide for installing software in ubuntu.

I would try to stick to software from synaptic if your not too sure what your doing.

if a program is installed but you dont find a shortcut for it try pressing alt+F2 and tryping the name of the program in the run box

---

### Post by Zwack on 2005-11-15
[QUOTE=bullfrog]also in add and applications it says the one there is installed. but i havent found on desktop any where. [/QUOTE]

Greetings,
    If you used Applications -> Add Applications to add an application then it will appear in the Applications Menu in the same place.

e.g. under Games I see Ataxx in both Applications -> Add Applications and in Applications -> Games.

I hope that this helps.

Z.

---

