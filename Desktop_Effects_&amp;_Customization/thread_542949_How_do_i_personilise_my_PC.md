---
title: "How do i personilise my PC?"
date: 2007-09-04
forum: Desktop Effects &amp; Customization
---

### Post by lunamystry on 2007-09-04
I have been playing my PC for a while now trying to change a few things:
[INDENT]-login screen(where I enter my password0[/INDENT]
[INDENT]-boot splash ( the one that has kubuntu ond a blue line underneath)[/INDENT]
[INDENT]-K-menu picture I would like to use the one in the picture[/INDENT]

I would like a graphical way if possible, every time i try to change these things with the terminal I mess up something. 

Thanks

---

### Post by Happy_Man on 2007-09-04
The icon, I know, is in a theme on kde-look called OS-K. The others, I'm not sure about.

---

### Post by Inxsible on 2007-09-04
you can go to kde-look and download a bunch of kdm login themes

[KDM Themes]("http://kde-look.org/index.php?xcontentmode=40")

for boot splash, the same website offers boot splashes too

[Boot Splash Screens]("http://kde-look.org/index.php?xcontentmode=61")

---

### Post by lunamystry on 2007-09-04
Uhm... with the icons thing I was kinda hoping to change it in a similar way that I change say the openoffice icons on the menu. I hope I make sense. I don't really want a new theme, i would like to just use the theme I have and change the Kmenu button the way i want. Not just one image. 

Don't I need KDM manager to run those themes? How do I download it?

---

### Post by por100pre1 on 2007-09-04
```
sudo aptitude install kdm
```

If it is already installed:

```
sudo dpkg-reconfigure kdm
```

and select KDM.

---

### Post by lunamystry on 2007-09-04
Where do i select KDM, nothing happens when i do what you said. 

[INDENT]lunamystry@alexis:~$ sudo apt-get install kdm
Reading package lists... Done
Building dependency tree
Reading state information... Done
kdm is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
lunamystry@alexis:~$ sudo dpkg-reconfigure kdm
lunamystry@alexis:~$ sudo dpkg-reconfigure kdm
lunamystry@alexis:~$

[/INDENT]

---

### Post by por100pre1 on 2007-09-04
**That means IMHO that KDM is already installed and working fine.**

Do you have gdm installed? 

```
aptitude search ^gdm
```

If there's an **i** before it, gdm is installed and you can do this:

```
sudo dpkg-reconfigure gdm
```

and select KDM

---

### Post by lunamystry on 2007-09-04
I doubt I have gdm, i am using Kubuntu which I clean installed. How do I access kdm graphically then? Its not not in k-menu>system setting>...

---

### Post by lunamystry on 2007-09-09
I want something like this (attachment) for my login manager or kdm. This one is not for feisty though. Is there one for feisty and gutsy.

---

### Post by lunamystry on 2007-09-09
How do I change grub? 

I found this  [http://http://www.kde-look.org/content/show.php/Kubuntu+Crystal+GRUB+splash+theme?content=31191]("http://http://www.kde-look.org/content/show.php/Kubuntu+Crystal+GRUB+splash+theme?content=31191")

I would like to do it to my PC but i have two hard drives dual booting one is feisty and the other gutsy. Which hard drive do i do it to? Will it work on my installations?

EDIT: i found it. I used 

        sudo apt-get install kdmtheme

and it gave me one of the things i was looking for. Now I need a graphical application to change my grub image.

---

### Post by lunamystry on 2007-09-09
Here is my little how to personilise Leonard'd desktop(or should it be how to install stuff needed to personilise Leonard's desktop)

One: Login screen

this needs the kdm theme manager or the gnome theme manager. I got this using```
sudo apt-get update 
sudo apt-get install kdmtheme
```

two: grub and boot screen:

for this i got startup-manager from  [http://http://www.getdeb.net/app.php?name=Startup+Manager]("http://http://www.getdeb.net/app.php?name=Startup+Manager") and it is thus easy to install. 
I installed it and since i couldnt find it I used 'alt+F2' and ran startupmanager and i changed what i needed.

Something I did that made startup manager not work was try to change grub in the wrong installation. The grub that was being used was from Gutsy as i installed it second and didn't change where grub should be. 

That is how I personilised my PC. Hope it helps someone.

---

