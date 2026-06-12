---
title: "Gnome won't install! D:"
date: 2010-06-02
forum: Desktop Environments
---

### Post by Zavie A. on 2010-06-02
So recently I've been exploring my options in terms of a desktop environment. trying out different options (Blackbox, Enlightenment ect..)
and somehow in the process i managed to uninstall Gnome.

Normally I would just re-install it but whenever I try I get this:

> sudo apt-get install gnome
[sudo] password for zavire: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  gnome: Depends: swfdec-mozilla but it is not going to be installed
E: Broken packages
 

So I go through synaptic and it tells me, to install 'swfdec-mozilla' i need to uninstall 'epiphany-extensions' so I do that. 
and then the terminal gives me the same error as before.. only it say that 'epiphany-extensions' is not going to be installed.

I'm running 10.04.
it's getting pretty annoying.
anyone have any ideas? :/

---

### Post by Isaacgallegos on 2010-06-02
Since I'm a noob the best advice I have is to reinstall Ubuntu. 
Next time use virtual box to test out new desktops and other experiments. It's free.

---

### Post by wojox on 2010-06-02
What if you try:

```
sudo apt-get install gnome-core
```

---

### Post by XubuRoxMySox on 2010-06-02
Or if you just want your original stuff back,

```
sudo apt-get install ubuntu-desktop
```

should do the trick.

-Robin

---

### Post by XubuRoxMySox on 2010-06-02
dumb satellite internet... disregard this, it was a duplicate (before I edited it)

---

