---
title: "How is Enlightenment different?"
date: 2008-06-15
forum: Desktop Environments
---

### Post by rainwalker on 2008-06-15
Besides it (supposedly) being faster, how is Enlightenment different from other window managers, mainly Gnome?
I ask because I'm setting up Ubuntu for one of my dad's friends on a little Fujitsu Lifebook, but it REALLY drags its heels running Ubuntu (and XFCE wasn't much better). I think it might have more to do with the crappy graphics driver than the comp's speed (800 Mhz processor), but things could definitely be snappier. I've heard good things about Enlightenment, so I was hoping someone could explain it's pros/cons or share their opinion of it :)

---

### Post by raul_ on 2008-06-15
First, Gnome is not a Window Manager, it's a Desktop Environment [http://en.wikipedia.org/wiki/Desktop_environment]("http://en.wikipedia.org/wiki/Desktop_environment")

[http://en.wikipedia.org/wiki/Window_manager]("http://en.wikipedia.org/wiki/Window_manager")

"How is Openbox different?

Answer that and add some "more configuation dialogs", "more eye-candy" and (in the future) more DE-like integration (File manager, Login manager, etc). 

I'm not saying that E17  is like Openbox (that would be a sacrilege) but they are both Window Managers, different between each other, but still Window Managers.

E17 aims to be a so called "Desktop Shell", but that is still under development, so nobody knows exactly what they mean.

There are more details like the EFL (enlightenment foundation libraries), that is part of Enlightenment, aimed to developers, but those details shouldn't concern the end user.

Also, read their "about" section, in their website ;)

EDIT:[http://www.enlightenment.org/p.php?p=about/e17&l=en]("http://www.enlightenment.org/p.php?p=about/e17&l=en") here

EDIT2: oh, there is also no (official) system tray in E17. Stubborness IMO, as I have seen people asking for this in a lot of forums, even the E17 ones, and the "hardcore" E17 users always come up with their theories, that don't convince me, but well, that's life, and they are on their own right of doing want they want

---

### Post by rainwalker on 2008-06-15
Sorry, I knew Gnome was a DE but I didn't know how else to say it. Would Nautilus be the WM? Or Metacity?

Can you recommend any lightweight WMs?

---

### Post by atomkarinca on 2008-06-16
The WM in Gnome is Metacity. If you turn on 3d effects it's replaced with Compiz.

My favorite WM is [Openbox]("http://icculus.org/openbox/index.php/Main_Page"). It's configured easily (with obconf), pretty lightweight and it integrates GTK and Qt applications very well. Then there is [Fluxbox]("http://fluxbox.sourceforge.net/"). The configuration is done with editing files but it's not hard to get the hang of. It has its own panel (which Openbox lacks). [LXDE]("http://lxde.sourceforge.net/") is a very nice DE, it's not lightweight as Openbox or Fluxbox but that's just because it comes preinstalled with a panel, lots of configuration tools and a menu :) It uses Openbox as its WM.

I haven't tried these exclusively but people love 'em: [AwesomeWM]("http://awesome.naquadah.org/"), [JWM]("http://joewing.net/programs/jwm/"), [DWM]("http://www.suckless.org/wiki/dwm/"), [IceWM]("http://www.icewm.org/").

---

### Post by ChameleonDave on 2008-06-16
Version 4 of KDE is more streamlined that than the old version (which is about the same as GNOME).  I'm getting good results with it at the moment, even though it is in beta.

Otherwise, try a super-lightweight manager such as Fluxbox.

---

### Post by urukrama on 2008-06-16
If you need a stable working environment, I don't recommend enlightenment (e17), which can still be a bit moody at times. Some people embrace e17 because they love they way it looks (I can't say I share that sentiment ;-)) and don't mind the bugs.

If you need a light reliable window manager, you could try Openbox or Icewm or even Xfce on a command-line install.

Openbox is a minimalistic window manager that is highly configurable. You can basically do anything you want with it, through third party applications (panels, etc.) Have a look at some screenshots in the monthly desktop thread; it contains quite a number of Openbox desktops. If you'd like to try out Openbox, follow the link in my signature.

Icewm is another light and flexible window manager, that emulates the standard Windows 98 look. The default themes are pretty ugly, but it isn't very hard to make it pretty. If you don't want to spend a lot of time configuring it, and need an environment that is friendly to those used to Windows, Icewm is probably the best choice. If you'd like to try Icewm, follow [aysiu's guide]("http://psychocats.net/ubuntu/").

Xfce can be pretty light and fast. Unfortunately, Xubuntu has become rather heavy, but if you'd like to try out a fast Xfce, I recommend doing a [command-line install]("http://psychocats.net/ubuntu/minimal") of Ubuntu and then install the package [xfce4]("http://packages.ubuntu.com/hardy/xfce4") (not [xubuntu-desktop]("http://packages.ubuntu.com/hardy/xubuntu-desktop")). You will have a very fast Xfce. I've done this on some older computers and don't notice a significant difference with simple window managers in terms of speed and responsiveness.

You'll get the best out of all the above if you do a [command-line install]("http://psychocats.net/ubuntu/minimal") of Ubuntu. It requires a little work and attention, especially after the installation, but if you want a fast Ubuntu install, have the time and want to learn something, it is the best way to go. 

Whatever choice you make, use light applications to keep the system light. You can still have a slow system with a light window manager if you use heavy applications. Thus, use Thunar, Rox-filer or PCManFM instead of Nautilus or Konqueror, a light media player over Amarok, etc.

---

### Post by TenPlus1 on 2008-06-16
I love using OPenBox and FbPanel for the startbar...  Very easy to configure using both obconf and obmenu...

---

### Post by PCMan on 2008-06-16
I'm pretty sure that LXDE is for you.
A lightweight yet user-friendly desktop environment.
It gives you features of modern desktops while it still runs on old machines with Pentium II CPU.
[http://lxde.org/](http://lxde.org/)

Here are some screenshots:
[http://lxde.org/screenshots.html](http://lxde.org/screenshots.html)

We have ubuntu repo.
```
deb http://ppa.launchpad.net/lxde/ubuntu hardy main
deb-src http://ppa.launchpad.net/lxde/ubuntu hardy main
```

apt-get lxde will give you this desktop environment.

Also, it's now used by Ubuntulite as default desktop environment.
You can install Ubuntulite, which is a lightweight variant of ubuntu.

---

### Post by rainwalker on 2008-06-16
Thanks everyone! I'll definitely look into these :)

---

### Post by Inxsible on 2008-06-16
> **rainwalker said:**
> Sorry, I knew Gnome was a DE but I didn't know how else to say it. Would Nautilus be the WM? Or Metacity?

Can you recommend any lightweight WMs?
Lightweight WM's are plenty.

1)Fluxbox
2)Openbox
3)Blackbox
4)PekWM
5)JWM
6)9wm
7)twm
8 )IceWM
9)LXDE
10)probably a million more

The best thing for you would be to install the Debian core or Ubuntu minimal and then install which ever WM you want on it.

That way it will have only the apps that you want and need instead of getting the default apps of any distro.

I have a Debian core + Fluxbox install and its great and snappy as hell. After entering the password and hitting enter, I am at the desktop in under 10 seconds.

---

### Post by Rui Pais on 2008-06-16
> **raul_ said:**
> ...
EDIT2: oh, there is also no (official) system tray in E17. Stubborness IMO, as I have seen people asking for this in a lot of forums, even the E17 ones, and the "hardcore" E17 users always come up with their theories, that don't convince me, but well, that's life, and they are on their own right of doing want they want

You make it sound like some conspiracy theory, *they* want to drive users to starving from systrays ;) :lol:

e17 simple don't implement one. Use a 3rd party stand alone or a 3rd party panel that implement one. Thats all.

---

### Post by raul_ on 2008-06-16
But it's true!!! :D

I just checked out the latest version from cvs and there are some nice modules additions, like for example the tiling mode module.Engage was also promising. I think E17 is becoming more mature and the philosophy is paying off.

I just saw that the aMsn developers will use EFL libraries to build (one of) the aMsn2 gui

Back to the topic, remember that when you install a Window manager you won't have a built-in File Manager, Image viewer, browser, etc. You'll have to install them separately

---

### Post by Inxsible on 2008-06-16
Yes, Once you install only a WM, you only get that and nothing else. So you will have to install the image viewer, file manager etc...

But that's the beauty of it. You can choose to install what you want as opposed to getting what the distro maker decided. That way you can keep your system as light as possible.

There are many options for doing something in terms of software. Here's a list which gives multiple lightweight options for different apps.

[http://users.skynet.be/six/gpure/tech/linux/apps.html](http://users.skynet.be/six/gpure/tech/linux/apps.html)

---

### Post by rainwalker on 2008-06-16
Hmm...do different WMs have better or worse hardware support? I ask because I'd be installing this on a fairly non-standard hardware since it's a subnotebook (different keyboard layout, resolution, etc).

---

### Post by raul_ on 2008-06-16
> **rainwalker said:**
> Hmm...do different WMs have better or worse hardware support? I ask because I'd be installing this on a fairly non-standard hardware since it's a subnotebook (different keyboard layout, resolution, etc).

Nope, that's under the hood

---

### Post by rainwalker on 2008-06-16
Uggg...this is going to be such a pain

Thanks everyone :)

---

