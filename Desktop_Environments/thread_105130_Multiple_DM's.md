---
title: "Multiple DM's"
date: 2005-12-17
forum: Desktop Environments
---

### Post by DJiNN on 2005-12-17
I have seen on other Linux machines the ability to have different desktop Managers (XFCE, Gnome, KDE, IceWM etc) & to switch between them, perhaps at boot time. Is this available for Ubuntu & how easy is it to achieve? I am currently using Gnome, which i like, but i also love XFCE & i would like to try KDE. Basically, i want to test a few different ones to see what one suits me the best, but i would like to switch between them until i eventually choose the one for me.  (If that makes sense?) :)

Any help, links info would be very much appreciated.

DJiNN

---

### Post by aysiu on 2005-12-17
This is what I would recommend:

Open up a terminal and type these commands ```
sudo apt-get update
sudo apt-get install kubuntu-desktop xubuntu-desktop
``` Before saying *yes* to installing all the packages, highlight which packages will be installed and copy them to a text file you save somewhere. Then, say *yes*. Log out. Click on *session* and select which desktop environment you want. Then log back in.

If you ever decide you want things back the way they were before, open up a terminal and type ```
sudo apt-get remove
``` then copy and paste all the items from the saved text file and hit *Enter*.

---

### Post by DJiNN on 2005-12-17
[QUOTE=aysiu]This is what I would recommend:

Open up a terminal and type these commands ```
sudo apt-get update
sudo apt-get install kubuntu-desktop xubuntu-desktop
``` Before saying *yes* to installing all the packages, highlight which packages will be installed and copy them to a text file you save somewhere. Then, say *yes*. Log out. Click on *session* and select which desktop environment you want. Then log back in.

If you ever decide you want things back the way they were before, open up a terminal and type ```
sudo apt-get remove
``` then copy and paste all the items from the saved text file and hit *Enter*.[/QUOTE]

Thanks ever so much for the info. I'm doing it right now, and although the connection has dropped a few times, resulting in me having to do the whole apt-get thing again, it seems to be working.... I guess i'll know soon enough? :)

I also did as you said about the list of software, so should i need to get rid of something, at least it won't be too difficult. :)

Many thanks indeed.

DJiNN

---

### Post by DJiNN on 2005-12-17
KDE sucks..... it looks great when you first see it, but it's just sooo cluttered. It's a choice between Gnome & XFCE.... i like em both, so i'm gonna live with them both for a while & see what one comes up trumps! :)

Any ideas (anyone) on how to remove just the KDE parts? 

Mega thanks for the help.....

DJiNN

---

### Post by aysiu on 2005-12-17
[QUOTE=DJiNN]
Any ideas (anyone) on how to remove just the KDE parts? [/QUOTE] Sure. Try [this](http://www.ubuntuforums.org/showthread.php?t=96048).

---

### Post by Redindian on 2005-12-17
Djinn,
I'm sure you are aware of the differrences between desktop environment and desktop managers.....I hope the following links will also help you for enlightening your gnome or xfce.

Gnome: [http://ubuntuforums.org/showthread.php?t=54476&highlight=enlightment](http://ubuntuforums.org/showthread.php?t=54476&highlight=enlightment)

XFCE: [http://ubuntuforums.org/showthread.php?t=101066](http://ubuntuforums.org/showthread.php?t=101066)

Have fun

---

### Post by anil_robo on 2005-12-18
Pehaps it's a vaguely related question, but still I'd ask it here.
**What is "clearlooks GTK theme engine" and how do I use it?**
THanks!

---

### Post by DJiNN on 2005-12-18
[QUOTE=aysiu]Sure. Try [this](http://www.ubuntuforums.org/showthread.php?t=96048).[/QUOTE]

Hi Aysiu. Thanks for that. Haven't tried it yet because i'm not sure if i want to completely uninstall ALL of the KDE programs..... i take it that it's possible to do that? Or do you have to have all or nothing? I'm not fussed if that's the case but thought i'd ask anyway. :)

Many thanks for all your help & input .... it's much appreciated.

DJiNN

---

### Post by DJiNN on 2005-12-18
[QUOTE=Redindian]Djinn,
I'm sure you are aware of the differrences between desktop environment and desktop managers.....I hope the following links will also help you for enlightening your gnome or xfce.

Gnome: [http://ubuntuforums.org/showthread.php?t=54476&highlight=enlightment](http://ubuntuforums.org/showthread.php?t=54476&highlight=enlightment)

XFCE: [http://ubuntuforums.org/showthread.php?t=101066](http://ubuntuforums.org/showthread.php?t=101066)

Have fun[/QUOTE]

Thanks for that Redindian.... I have tried elive (a few months ago) & i really like Enlightenment..... E17 is stunning, but E16 is VERY good also. I'm not sure if i have the "Bravado" to give it a go yet, as although i'm learning fast, i'm still very new to Ubuntu & although i'm not new to computers per se, i am still a newbie when it comes to using Linux & have much to learn.... :)

But i shall keep it in mind & who knows? :) I've still got to choose between Gnome or XFCE yet, and i'm not sure which one is for me because i like them both..... there's something about XFCE that's just great.... & there's something about Gnome that's great!! :) If only i could combine the bits from both that i like eh? :)

DJiNN

---

### Post by aysiu on 2005-12-18
[QUOTE=DJiNN]Hi Aysiu. Thanks for that. Haven't tried it yet because i'm not sure if i want to completely uninstall ALL of the KDE programs..... i take it that it's possible to do that? Or do you have to have all or nothing? I'm not fussed if that's the case but thought i'd ask anyway. :)[/QUOTE] Well, it's a copy and paste list of programs. What you could do is copy and paste it (yes, to a text file), then delete the programs you want to keep, and **then** copy and paste the revised into the terminal after ```
sudo apt-get remove
```

---

