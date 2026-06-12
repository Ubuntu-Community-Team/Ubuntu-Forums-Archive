---
title: "ubuntu 12.10 gdm problem"
date: 2012-11-05
forum: Desktop Environments
---

### Post by alvpizz on 2012-11-05
hello, i am using ubuntu 12.10, and i have installed many desktop environments in addition unity, the default one. my problem is that now, in the gdm, when i click on the ubuntu icon to select the desktop environment i want to use, the list is quite long, and it goes beyond the end of the screen, so I can select no desktop environment, because I can't click anymore on the ok at the bottom of the list.
i have installed GNOME, gnome classic, lubuntu-desktop and xubuntu-desktop. i have also tried to remove them, but they still not disapper from the list.:confused:
i would not like to re-install my system, so I would like to have an easy solution to this..

by the way, now, when i start and switch off the computer, i get no more the purple sceen with written ubuntu and the five dots under it, but i get the lubuntu blue screen.

does anyone know how to solve this:mad:? thankyou!

---

### Post by danelwillis on 2012-11-05
You might have installed an old version ox Linux, ihad this problem you can remove the different packages using synaptic manager, if you don't have this try "sudo apt-get install synaptic" you should be able to delete the packages relating to the different environments

---

### Post by alvpizz on 2012-11-05
> **danelwillis said:**
> You might have installed an old version ox Linux, ihad this problem you can remove the different packages using synaptic manager, if you don't have this try "sudo apt-get install synaptic" you should be able to delete the packages relating to the different environments

i have already removed all the installed packages that i could found using synaptic searching with it "xubuntu" and "lubuntu". now none of them are installed

---

### Post by alvpizz on 2012-11-05
I'de managed to resolve the problem: i have uninstalled also all packages found by searching in synaptic "xcfe" and "lxde". 
anyway, one problem still remains: if i have installed more than 7 desktop environments, the list on the gdm runs out of space and i can not choose anymore. this problem should be fixed.

---

### Post by ibjsb4 on 2012-11-05
I think I would try "lightdm" just to see if it handles the list differently.  I have used lightdm with the gnome-classic desktop without problems.  It is also default for xubuntu/lubuntu and unity.  I do not run gnome-shell so don't know about that.

---

### Post by alvpizz on 2012-11-05
> **ibjsb4 said:**
> I think I would try "lightdm" just to see if it handles the list differently.  I have used lightdm with the gnome-classic desktop without problems.  It is also default for xubuntu/lubuntu and unity.  I do not run gnome-shell so don't know about that.

and how can I see if i have installed gdm or lightgdm? and how can I switch from one to the other?

---

### Post by ibjsb4 on 2012-11-05
Googlubuntu is good for forum searches.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=switch+from+gdm+to+lightdm&as_qdr=all&sa=Google+Search&lang=en]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=switch+from+gdm+to+lightdm&as_qdr=all&sa=Google+Search&lang=en")

You probably have lightdm installed, check to see with the software center or just try to install it in terminal.

sudo apt-get install lightdm

If its already installed, it will say so.

And I think you will find this interesting  :)

[http://www.psychocats.net/ubuntu/pureubuntu](http://www.psychocats.net/ubuntu/pureubuntu)

---

