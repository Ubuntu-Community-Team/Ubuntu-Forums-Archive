---
title: "[SOLVED] Window Managers"
date: 2008-08-03
forum: Desktop Environments
---

### Post by diego898 on 2008-08-03
I am new to ubuntu. I know there are a number of window managers out there. X? Fluxbox? KDE? etc? My question is, WHY are there different window managers? WHY would I switch from gnome? If the progs are all transferable, then why are there multiple? I understand some are made for lower end machines. My machine runs gnome fine so does it even bother me to experiment around with them? And if it does, then how do I do that?

---

### Post by blue_shift on 2008-08-03
1. Why are there different managers?

For the same reason that there are different linux distributions: choice. WMs have different features, options, etc. and also have different programmes bundled with them, eg. different text-editors.

Xfce intends to use minimal system resources.
KDE is more feature-rich than gnome in terms of options and configuration, as well as historically more graphically impressive.

Some apps are specific to environments, eg. the media player amarok is built with KDE in mind (built on qt3, not gtk+). You can use amarok under gnome, but qt3 must then run alongside gtk+. This means that kde apps are slower and more buggy under gnome and vice versa.

Basically, it's a matter of personal choice, and once you get to grips with using ubuntu in general you should try KDE, Xfce, and see which you like the most.

2. How does one try different managers?
```
sudo apt-get install kde-desktop
```
Or 
```
sudo apt-get install xfce-desktop
```

---

### Post by BGFG on 2008-08-03
It's just about people excercising the power of choice. And amazing programmers sharing their skills. A manager is a manager, but for different individuals a few settings may make all the difference in the world. More configurability, faster behavior. If you like what you have then stick with it, but there's no harm in trying something new...The cool thing about linux is that you can.
I myself recently tried Enlightenment, and disliked it greatly. 
It was fun as hell though.

I'm a GNOME man myself, and just don't like KDE libraries on my machine.

---

### Post by bodhi.zazen on 2008-08-03
See also:

[http://xwinman.org/](http://xwinman.org/)

Other then the big 3 (KDE, Gnome, and XFCE) you will most likely want to learn how to customize the alternate WM.

---

### Post by diego898 on 2008-08-03
On that site, it sais window managers for x, and has another category for desktopns. What is the difference between a window manager and a desktop? I think what will help me is:

Gnome - What is it in relation to:
Metaticy - what is it:
Nautilis - What is it


X - WHAT IS IT!

---

### Post by Ru$$i@N on 2008-08-03
x is, i guess, the visual server? :) i'm still learning myself.

back to WMs. I found Awesome WM for myself, takes some getting used to, but was an easy switch from Fluxbox. I have it on my laptop on top of Xubuntu with Xfce. Awesome - is pretty much for those who mostly don't need the mouse :D

---

### Post by bodhi.zazen on 2008-08-03
In a nut shell, a window manager is the graphical interface, the boxes and "windows" + an interface for keyboard and mouse.

A desktop environment is a window manager + applications.

gnome has gedit for example, and kde has kate ...

---

### Post by diego898 on 2008-08-03
so if I install kde-desktop, then use it, decide I like it, how do I switch over to it COMPLETELY and remove gnome? How can I do the same for XFCE?

---

### Post by pbpersson on 2008-08-03
> **bodhi.zazen said:**
> 
gnome has gedit for example, and kde has kate ...

Gnome has Gedit, KDE has Kate
Gnome has Nautilis, KDE has Dolphin

However, I like Gedit so I use that on KDE and I like Dolphin so I use that on Gnome.

So.....now we can REALLY confuse the newbies.  ;)

---

### Post by BGFG on 2008-08-03
> **diego898 said:**
> so if I install kde-desktop, then use it, decide I like it, how do I switch over to it COMPLETELY and remove gnome? How can I do the same for XFCE?

basically is a matter of sudo apt-get or aptitude soooooo:
```

sudo apt-get install xfce-desktop
sudo apt-get install kde-desktop
sudo aptitude install xfce-desktop
sudo aptitude install kde-desktop

```
install your desktops

and
```

sudo apt-get remove xfce-desktop
sudo apt-get remove kde-desktop
sudo aptitude remove xfce-desktop
sudo aptitude remove kde-desktop

```

remove them, once you decide on which one you like.

And i case you're wondering as to the difference between the apt-get and aptitude commands, well there isn't really. Nothing MAJOR at least :) for clarification check this

[http://ubuntuforums.org/showthread.php?t=855569](http://ubuntuforums.org/showthread.php?t=855569)

---

### Post by diego898 on 2008-08-03
> **BGFG said:**
> basically is a matter of sudo apt-get or aptitude soooooo:
```

sudo apt-get install xfce-desktop
sudo apt-get install kde-desktop
sudo aptitude install xfce-desktop
sudo aptitude install kde-desktop

```
install your desktops

and
```

sudo apt-get remove xfce-desktop
sudo apt-get remove kde-desktop
sudo aptitude remove xfce-desktop
sudo aptitude remove kde-desktop

```

remove them, once you decide on which one you like.

And i case you're wondering as to the difference between the apt-get and aptitude commands, well there isn't really. Nothing MAJOR at least :) for clarification check this

[http://ubuntuforums.org/showthread.php?t=855569](http://ubuntuforums.org/showthread.php?t=855569)

so do I use BOTH apt-get and aptitude or either one?

---

### Post by diego898 on 2008-08-03
The 

sudo aptitude install kde-desktop 

command said that it couldnt find any package whose name or description matched.Any ideas?

---

### Post by diego898 on 2008-08-03
can anyone please help me with this? I think it could be because I dont have the proper repositories

---

### Post by Ingenue on 2008-08-03
Ok. I'm kind of confused now. This is how I thought it was.

Gnome or KDE: Desktop environment

X: is program creating windows on top of GNOME.

X Win. Manager: Controls the nature of the windows in x, Customize,         effects, how you interact with the windows...

Did I just pull this out of you know where??

---

### Post by p_quarles on 2008-08-03
> **Ingenue said:**
> Ok. I'm kind of confused now. This is how I thought it was.

Gnome or KDE: Desktop environment

X: is program creating windows on top of GNOME.

X Win. Manager: Controls the nature of the windows in x, Customize,         effects, how you interact with the windows...

Did I just pull this out of you know where??
Sort of. X is the bottom-level application on top of which the entire graphical environment runs. It does basic things like define how the monitor and the mouse and keyboard (or other HIDs) interact with things on the screen. It is a framework more than an environmet. 

The window manager is the application needed for basic windowing of applications. E.g., you don't need KDE or Gnome in their entirety to run a graphical environment: you just need something that provides the windowing capability. 

The DEs are really feature-rich application suites that are meant to eliminate the need for a lot of set up.

---

### Post by Ingenue on 2008-08-03
Thanks for clearing that up. :)

---

### Post by diego898 on 2008-08-04
So to install kde for example, I would use what command exactly? Because in using the one given to me earlier, it didnt work.

---

### Post by Oldsoldier2003 on 2008-08-04
> **diego898 said:**
> So to install kde for example, I would use what command exactly? Because in using the one given to me earlier, it didnt work.

```
sudo apt-get install kubuntu-desktop
``` will sort you.

---

### Post by billgoldberg on 2008-08-04
> **blue_shift said:**
> 1. Why are there different managers?

For the same reason that there are different linux distributions: choice. WMs have different features, options, etc. and also have different programmes bundled with them, eg. different text-editors.

Xfce intends to use minimal system resources.
KDE is more feature-rich than gnome in terms of options and configuration, as well as historically more graphically impressive.

Some apps are specific to environments, eg. the media player amarok is built with KDE in mind (built on qt3, not gtk+). You can use amarok under gnome, but qt3 must then run alongside gtk+. This means that kde apps are slower and more buggy under gnome and vice versa.

Basically, it's a matter of personal choice, and once you get to grips with using ubuntu in general you should try KDE, Xfce, and see which you like the most.

2. How does one try different managers?
```
sudo apt-get install kde-desktop
```
Or 
```
sudo apt-get install xfce-desktop
```

KDE and XFCE are DE's, not WM's.

List of WM's:

[http://xwinman.org/](http://xwinman.org/)

--

I personaly use Fluxbox.

Why?

To start it much, much faster than kde, gnome and xfce.

It's more customizable. 

Just adjust the text file to suit you.

I can create my own keyboard shortcuts, make my own menu, ...

The fluxbox link in my signature might be worth a read, to get the idea in use between an gnome destkop, and a fluxbox desktop.

---

### Post by RadenMu'az on 2008-08-04
WM is basically a program that put applications into 'windows' so you can drag them around the desktop, resize, hide, etc.

It DOES NOT control the applications' GUI and widgets (buttons, checkboxes, etc.)
Those are managed by the running apps itself. For example, Gedit uses [Gnome/GTK]("http://en.wikipedia.org/wiki/GTK%2B") for its widgets. Kate meanwhile uses [Qt]("http://en.wikipedia.org/wiki/Qt_(toolkit)") for those.

I have some experience when a WM crash and saw applications still running perfectly but with no WM and they all look 'borderless'.
Then, I cannot use other running apps, bring to top, move around etc. It's a really bad experience until I started [Openbox]("http://http://icculus.org/openbox/index.php/Main_Page") (a WM) to save the horrible situation.

--

There are a lot of lightweight/minimalistic WM out there. They run great on your old <1Ghz computers.
To name a few: Openbox, Fluxbox, IceWM, PekWM and Awesome 


I prefer Openbox to Fluxbox.
Openbox is just a WM, unlike Fluxbox that has wallpaper manager, panel, etc.
Also, it is easier for beginner as it has it GUI Configuration manager, ObConf, to set themes, margins, text size, etc.

As Openbox is nothing but WM, I can add those custom pagers, panels, dockapps later, like [Pypanel]("http://pypanel.sourceforge.net/"), [Tint2]("http://code.google.com/p/tint2/"), etc.


Install minimalistic Window Manager:
sudo apt-get install fluxbox
sudo apt-get install openbox
sudo apt-get install icewm
sudo apt-get install awesome

---

### Post by diego898 on 2008-08-05
why must I use apt-get to install instead of aptitude?

---

### Post by bodhi.zazen on 2008-08-05
> **diego898 said:**
> why must I use apt-get to install instead of aptitude?

You may use any tool you wish to install. apt-get, aptitude, synaptic, Add/Remove , etc ...

There are (small) differences between them and it is at the end of the day personal preference.

---

### Post by mikjp on 2008-08-06
> **diego898 said:**
> My machine runs gnome fine so does it even bother me to experiment around with them? 

Because:

a) it is fun
b) you learn something
c) you will soon be bored with GNOME
d) they all look different
f) some of them are lighter than GNOME
g) KDE is better than GNOME ;)
h) you can install twm to see what linux looked like in the mid 1990s
i) you are free to do anything with your system

But you don't have to, if you don't want to. 

Greetings,

mikko

---

### Post by jviscosi on 2008-08-07
> **diego898 said:**
> so if I install kde-desktop, then use it, decide I like it, how do I switch over to it COMPLETELY and remove gnome? How can I do the same for XFCE?

Bear in mind that if you really do completely remove Gnome, it will take a bunch of other programs with it that you might still want to use in KDE (or whatever).  I have both KDE and Gnome (and XFCE and Fluxbox and ...) on my machine even though I usually run PekWM, because I use programs from various DEs and WMs.

---

### Post by zaddik01 on 2008-08-07
> **mikjp said:**
> Because:

a) it is fun
b) you learn something
c) you will soon be bored with GNOME
d) they all look different
f) some of them are lighter than GNOME
g) KDE is better than GNOME ;)
h) you can install twm to see what linux looked like in the mid 1990s
i) you are free to do anything with your system

But you don't have to, if you don't want to. 



This is a great post!! 

I think there are several questions that should be asked.

1. Are you new to Linux? If you are, I think you can stick with the big 3 (gnome, kde, and xfce). They are closest to Windows and are generally very easy to use. After you have gotten comfortable with Linux and the command line, you can start to branch out. 

2. What do you want to DO with Linux? This is where it gets messy. Some people are honestly trying to get away from Microsoft products for business or personal reasons. I would suggest you stick with the big 3 as they are more designed to ease the transition. They have the best integration with the "Office" apps. Some people are just playing around with something different, and some people are just trying to learn about computers and programming. If you are in the latter two categories then hopefully you don't mind messing under the hood and don't mind if something breaks on you. 

Most of the other WMs will come up with pretty much a blank desktop. The application menus come from right clicking on the desktop. That can be a real head turner if you aren't prepared. They generally require some work to get looking nice and customized, but there are tons of sites with themes and applettes galore. Over the last 10 years of using Linux I have used TWM, FVWM, Afterstep, WindowMaker, Gnome, KDE, XFCE, and all of the *box variants. For the last two years I have been using fluxbox. I am a Windows programmer by day, so I enjoy a spartan desktop at night :)

---

### Post by loligager on 2008-08-08
Try them all out i say
Kde is well a memory hog so i you have less ram go with Xfce
I think the best is gnome
this is very cool
sudo apt-get install ubuntustudio-desktop

Really good

---

### Post by mikjp on 2008-08-08
> **zaddik01 said:**
> Most of the other WMs will come up with pretty much a blank desktop. The application menus come from right clicking on the desktop. That can be a real head turner if you aren't prepared. They generally require some work to get looking nice and customized, but there are tons of sites with themes and applettes galore. 

I have found the [Gentoo Wiki](http://gentoo-wiki.com/Main_Page) to be useful when tweaking the window managers to look nicer. True, it is Gentoo Documentation, but the window managers in Ubuntu are the same as in Gentoo.

You can find a lot of links in [xwinman.org](http://xwinman.org/). [This](http://www.junauza.com/2008/08/20-most-nimble-and-simple-x-window.html), on the other hand, shows you how plain the window managers are without any customization.

Greetings,

mikko

---

### Post by benign on 2008-08-08
It seems to be:

```

sudo apt-get install kde4

```

instead of kde-desktop.

---

### Post by MattBD on 2008-08-17
IceWM is a great window manager. I've found the likes of Fluxbox to be a bit too mouse-oriented for my liking, but IceWM is very easy to use with keyboard shortcuts - you can use the Super key(the Windows key on most keyboards) to open the main menu like in Windows, then go through the different menus quickly by pressing more keys, such as A for Applications, N for Network etc, and it has a handy built-in launcher that you can use by hitting Super+Space then typing the name of the application. It's also easy to get the hang of as it resembles Windows, it's easy to theme and although you really need to edit text files to configure it, it's very easy. It's an ideal introduction to minimal window managers.
If you want to try it, check out [this link]("https://help.ubuntu.com/community/IceWM") for more details on using it.

---

