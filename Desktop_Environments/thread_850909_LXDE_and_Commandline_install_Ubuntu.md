---
title: "LXDE and Commandline install Ubuntu"
date: 2008-07-06
forum: Desktop Environments
---

### Post by Idzme on 2008-07-06
I tried to do a commandline install (for an minimal ubuntu install) and want to have lxde as an desktop enviroment. But when I add the repos and update and then type in the terminal:

sudo apt-get install lxde I got the following message:
De volgende pakketten hebben niet-voldane vereisten:
  lxde: Vereisten: gpicview (>= 0.1.9) maar het is niet installeerbaar
        Vereisten: lxappearance (>= 0.2) maar het is niet installeerbaar
        Vereisten: lxpanel (>= 0.2.7.2) maar het zal niet geïnstalleerd worden
        Vereisten: lxsession-lite (>= 0.3.5) maar het is niet installeerbaar of
                   lxsession (>= 0.3) maar het is niet installeerbaar
        Vereisten: openbox (>= 3.4.6.1) maar het zal niet geïnstalleerd worden
E: Niet-werkende pakketten:
bas@xfce4:~$ 

It's in dutch but he tells me he cannot install the package you see above.

In a full ubuntu install it did work, why didn;t it work in a commandline system?

---

### Post by Dicinox on 2008-07-07
try sudo aptitude install lxde

Sorry, my english is to bad, so and gonna try to explain.

When you make a minimal ubuntu's install, before to install a desktop envoriment you have to install the X system so when you try to install lxde whitout the X system it failed. whit aptitude you solve that because it manage better the dependecies.



(In spanish: cuando haces una instalación minima de ubuntu antes del desktop tienes que instalar las X, aptitude maneja mejor las dependencias e instala todo lo que necesitas para instalar lxde)

---

### Post by Idzme on 2008-07-07
> **Dicinox said:**
> try sudo aptitude install lxde




I did, did not work, same error as before!
thanks for you're reply

---

### Post by atomkarinca on 2008-07-07
Have you installed xorg first?

```
sudo apt-get install xorg
```

[Here]("http://www.psychocats.net/ubuntu/minimal")'s a nice howto from aysiu. He explains how to install a minimal system with IceWM. Instead of IceWM you can install LXDE

---

### Post by Idzme on 2008-07-07
> **atomkarinca said:**
> Have you installed xorg first?

```
sudo apt-get install xorg
```

[Here]("http://www.psychocats.net/ubuntu/minimal")'s a nice howto from aysiu. He explains how to install a minimal system with IceWM. Instead of IceWM you can install LXDE

That's what I did, command line install with Icewm and rox-filer. Then add the repo's of lxde and then:
sudo apt-get install lxde

did not work, see error messages in first post

---

### Post by atomkarinca on 2008-07-07
I don't understand the messages but it seems like it's complaining about the versions of those applications. Which guide are you using to install LXDE? It might be an old repository.

---

### Post by Dicinox on 2008-07-10
Did you install xserver-xorg? Lxde is a meta-package, try installing lxsession-lite whit aptitude...

Waht else have you installed?

---

