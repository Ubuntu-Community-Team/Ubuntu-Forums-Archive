---
title: "Desktop icons Lost after Elementary Desktop Installation"
date: 2013-02-20
forum: Desktop Environments
---

### Post by rushikesh988 on 2013-02-20
Recently I have found that we can install the elementary environment on ubuntu .
I installed it using
> sudo apt-get install elementary-desktop
some of its packages got installed but some gave me error
> The following packages have unmet dependencies:
 elementary-artwork : Depends: elementary-theme but it is not going to be installed


now the problem is since I have installed that desktop environment I have lost the Desktop icons in unity .
Also My computer became slow .
I have tried to unistall the the elementary desktop by:
> sudo apt-get remove elementary-desktop
which returned
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 elementary-artwork : Depends: elementary-theme but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution)

and I have also tried to fix the broken/unment dependencies :
by trying 
> apt-get -f install
but no effect


please Help me I want to remove elementary environment and Also I want to get back the gnome desktop icons.

---

### Post by rushikesh988 on 2013-02-22
anybody

---

### Post by Frogs Hair on 2013-02-22
Elementary is now known as the Pantheon desktop and you would have had to use a PPA in order to get the needed dependencies for 12.10.
[http://linuxmotion.com/tutorials/73-how-to-install-pantheon-desktop-enviroment-in-ubuntu-12-10](http://linuxmotion.com/tutorials/73-how-to-install-pantheon-desktop-enviroment-in-ubuntu-12-10)

It looks like what  you may have installed is the artwork because I see that in synaptic,but nothing titled elementary-desktop  . Below are the Compiz and Unity reset commands. If the terminal is not available with Ctrl + Alt + T then you may have to use Ctrl + Alt+ F1 and try from TTY. 

[http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html](http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html)

---

