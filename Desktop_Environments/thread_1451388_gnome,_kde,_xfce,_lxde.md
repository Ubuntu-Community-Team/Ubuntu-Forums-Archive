---
title: "gnome, kde, xfce, lxde"
date: 2010-04-10
forum: Desktop Environments
---

### Post by lanceflame44 on 2010-04-10
This is a tutorial on how to get all of the desktop enviroments used in ubuntu.
I do not know how to completly remove them.
use the command
"sudo apt-get install kubuntu-desktop" to install kde
"sudo apt-get install xubuntu-desktop" to install xfce
"sudo apt-get install lubuntu-desktop" to install lxde
"sudo apt-get install ubunut- desktop" to install gnome
and here is another thing i figured out...
to upgrade to linux mint (including default software/packages) from a gnome installation of ubuntu add the mint sources for your distribution (ex. for karmic koala use the mint helena sources) and go in synaptic package manager and install the package "mint-meta-main"
to switch between the desktop enviroments click on the user on the login screen and on the bottom there should be a drop down menu and you can select what desktop enviroment you want to use.
**note**
upgrading to linux mint is hard to reverse and it upgrades your current gnome desktop and does not add a option in the drop down menu.
**upgrading to mint tested and working on karmic koala
**all desktop enviroments tested and working on lucid lynx beta 2

---

### Post by Paddy Landau on 2011-03-16
Thank you for those instructions.

If I install [lubuntu-desktop]("apt:lubuntu-desktop"), is it really as easy as switching between LXDE and Gnome each time I log in?

Will using LXDE for a while mess up my Gnome settings at all, or when I log back into Gnome will it be just as I left it?

I use Ubuntu Lucid 10.04 64-bit.

---

### Post by kellemes on 2011-03-17
> **lanceflame44 said:**
> This is a tutorial on how to get all of the desktop enviroments used in ubuntu.
I do not know how to completly remove them.
use the command
"sudo apt-get install kubuntu-desktop" to install kde
"sudo apt-get install xubuntu-desktop" to install xfce
"sudo apt-get install lubuntu-desktop" to install lxde
"sudo apt-get install ubunut- desktop" to install gnome


This is just not true..
These instruction will not simply install other desktop environments, they will install other distributions, even if they are based on the same engine.

In order to install Lxde for example you simply do..
```
apt-get install lxde
```
And choose Lxde as session from your loginscreen..
This way your Ubuntu-experience will not be dramatically changed when you decide to uninstall Lxde.

If you decide to keep using Lxde you can always install lubuntu-desktop, this will probably install a lot of extra packages in order to make the Lxde-experience complete. Well, with Lxde it won't be much but there is a major difference between installing kubuntu or KDE.

---

### Post by Paddy Landau on 2011-03-17
Ah, so if I want to use LXDE (rather than Lubuntu), I simply install [lxde]("apt:lxde"). Then each time I log in, I can choose between LXDE and Gnome. Have I understood correctly?

---

### Post by kellemes on 2011-03-17
> **Paddy Landau said:**
> Ah, so if I want to use LXDE (rather than Lubuntu), I simply install [lxde]("apt:lxde"). Then each time I log in, I can choose between LXDE and Gnome. Have I understood correctly?

Yes. And your current Gnome/Ubuntu-experience will not be touched.

More info on LXDE, how to configure etc..
[http://wiki.lxde.org/en/Main_Page]("http://wiki.lxde.org/en/Main_Page")

---

### Post by Paddy Landau on 2011-03-17
> **kellemes said:**
> Yes. And your current Gnome/Ubuntu-experience will not be touched.
Fantastic. I will try it. Thank you again.

---

### Post by Paddy Landau on 2011-03-17
I've tried it, and it works well bar one problem.

The monitor setting is a low resolution. I fix it with System > Monitors; but that seems to confuse the desktop. When I log out and log in again, the monitor is reset to the default low resolution, so I again have to set it and again get a confused desktop.

Do you know how to set the monitor setting permanently?

Thanks.

---

### Post by kellemes on 2011-03-17
Try lxrandr, it should have been installed with Lxde.

---

### Post by Paddy Landau on 2011-03-18
> **kellemes said:**
> Try lxrandr, it should have been installed with Lxde.
Unfortunately, that gives me exactly the same as System > Monitors. I tried it, but had the same results; the desktop gets confused, and the settings are lost on logging out.

---

### Post by Paddy Landau on 2011-03-18
It's OK, I found [the answer]("http://ubuntuforums.org/showthread.php?t=1536228").

Thanks for all your help.

---

### Post by steph291 on 2011-09-22
> **lanceflame44 said:**
> This is a tutorial on how to get all of the desktop enviroments used in ubuntu.
I do not know how to completly remove them.
use the command
"sudo apt-get install kubuntu-desktop" to install kde
"sudo apt-get install xubuntu-desktop" to install xfce
"sudo apt-get install lubuntu-desktop" to install lxde
"sudo apt-get install ubunut- desktop" to install gnome
and here is another thing i figured out...
to upgrade to linux mint (including default software/packages) from a gnome installation of ubuntu add the mint sources for your distribution (ex. for karmic koala use the mint helena sources) and go in synaptic package manager and install the package "mint-meta-main"
to switch between the desktop enviroments click on the user on the login screen and on the bottom there should be a drop down menu and you can select what desktop enviroment you want to use.
**note**
upgrading to linux mint is hard to reverse and it upgrades your current gnome desktop and does not add a option in the drop down menu.
**upgrading to mint tested and working on karmic koala
**all desktop enviroments tested and working on lucid lynx beta 2
OMG start job 'apt-get install ubuntu-desktop'
217 mb download, 900 mb will be used on hd :popcorn:
hope it will work fine really...
using lubuntu on a thinkpad a21m
40gb hd, 512mb ram

---

### Post by amjjawad on 2011-09-22
Sorry but what's the point of having all of them? for new comers, this will be VERY confusing!!!!!

---

### Post by Paddy Landau on 2011-09-22
> **amjjawad said:**
> ... what's the point of having all of them?
Some people love to play and experiment with different types of desktop. Use it only if you are one of those.

The commands cannot hurt; all they do is use a little extra disk space.

---

### Post by amjjawad on 2011-09-22
> **Paddy Landau said:**
> Some people love to play and experiment with different types of desktop. Use it only if you are one of those.

The commands cannot hurt; all they do is use a little extra disk space.

Totally understood but check my 2nd part of my post ;)

---

### Post by Paddy Landau on 2011-09-22
> **amjjawad said:**
> Totally understood but check my 2nd part of my post ;)
Yeah, OK, confusion is what comes before understanding...

---

### Post by amjjawad on 2011-09-22
> **Paddy Landau said:**
> Yeah, OK, confusion is what comes before understanding...

For me, there are other ways to learn and understand. 
The best about Linux is you can do one thing in too many ways/approaches but again, for me as LXDE Forum Moderator and a member in both LXDE and Lubuntu, I need to use the easiest and the simplest approach to help others, especially new comers. 
I'm just sharing "my opinion", that's all.

:)

---

### Post by Krytarik on 2011-09-22
> **amjjawad said:**
> The best about Linux is you can do one thing in **too many** ways/approaches but again, for me as LXDE Forum Moderator and a member in both LXDE and **Lubuntu**, I need to use the easiest and the simplest approach to help others, especially new comers.
So, you are basically saying, "Canonical, please keep Lubuntu and drop all the others."? :P

Greetings.

---

### Post by amjjawad on 2011-09-22
> **Krytarik said:**
> So, you are basically saying, "Canonical, please keep Lubuntu and drop all the others."? :P

Greetings.

Definitely not what I meant ;)

---

### Post by Krytarik on 2011-09-22
> **amjjawad said:**
> Definitely not what I meant ;)
Then what, focus on only Ubuntu?

---

### Post by amjjawad on 2011-09-22
> **Krytarik said:**
> Then what, focus on only Ubuntu?

Apparently, we're talking apples and oranges here!

If you have installed more than one DE on your system, you may understand what I was referring to.
To learn more about a DE or a Distro, there are different approaches which are beyond the scope of this thread. I don't prefer to discuss that here. 

All what I wanted is to share is my opinion about this thread. What so hard to understand about that? :)

---

### Post by Krytarik on 2011-09-22
> **amjjawad said:**
> If you have installed more than one DE on your system, you may understand what I was referring to.
Yeah, right! But no-one is forced to install all of those meta-packages into one system.

So, after the "new comer", you are referring to, made his choice for one of the variants of Ubuntu available as install images, and installed it, he doesn't have to install any of the other variants via their respective meta-packages at all!

So, your point of confusing new comers now makes even less sense then before.

---

