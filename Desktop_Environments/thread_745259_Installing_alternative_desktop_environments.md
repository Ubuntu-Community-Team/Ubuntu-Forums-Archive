---
title: "Installing alternative desktop environments"
date: 2008-04-04
forum: Desktop Environments
---

### Post by Ozor Mox on 2008-04-04
I am running Ubuntu 7.10 and would like to install some alternative desktop environments. Specifically XFCE for my slow study PC, and KDE for my faster PC, and be able to choose which to start up from the login screen. A couple of questions about this...

1. Do you recommend installing the desktop packages kubuntu-desktop and xubuntu-desktop, or using the original packages kde and xfce4? From my understanding, using *-desktop will give me a set up desktop, whereas with the base packages I will need to configure the desktop to my tastes. My only reservation with kubuntu-desktop is that people have said Kubuntu isn't a very good KDE implementation (particularly something about it breaking some options on Konqueror), maybe I'd be better configuring it how I want it?

2. Other than hard disk space and cluttered menus, installing a different desktop environment will not use up any other additional resources on my computer will it?

This is all assuming that I'm right in thinking that kubuntu/xubuntu-desktop are just Ubuntu's own customised KDE/XFCE environments.

---

### Post by Jimmey on 2008-04-04
Assuming you have a capable internet connection and you're looking to do new installs on two computers, try downloading the xubuntu and kubuntu CD's separately. This might save a lot of hassle.

kdebase will just provide the desktop environment - kubuntu-desktop will provide that, and all of the applications usually provided with it. It depends which applications you want to use. For xfce, I would recommend just installing the base package ontop of Gnome, as this makes little difference.

---

### Post by kerry_s on 2008-04-04
1. i recommend you just grab the environment->
sudo apt-get install xfce4
sudo apt-get install kde-core

2. of course it will, depends what's running. for instance the kde stuff is made to work together, when you run a kde item all the kde stuff starts as well. xfce4 is not bad, not much overhead there.

the real power of customizing is in the wm's, depending which 1, you can pick mostly everything you want to make up your setup.

for instance my laptops 450mhz 256mb ram, so i build it for low resource and speed. i use jwm for my wm, it's really light, but has alot of the desktop features, so i don't have to use extra programs for that. i use known light programs, such as rox-filer for file manager, leafpad for editor, etc...
i have full control of everything, i can even do the menu's my way.

most people tend to go for the *box's though, as jwm is a young wm, but i believe most of the lite distro's will switch to jwm because it has fantastic features yet is rock solid and lower on resources than the *box's.

---

### Post by RedSquirrel on 2008-04-04
I agree with the recommendation of kerry_s to install the environment itself, not the desktop metapackage.

If you install the *-desktop metapackage, you get all the applications as well and you probably don't want all of that.

I don't use KDE, but I can say from my experience that setting up Xfce to your taste is really easy. It's just point & click.

Have a look at the xfce4 package information to see what it recommends for additional Xfce-specific packages (e.g., xfce4-terminal, xfce4-mixer, etc.). You can install those things too, if you like. xfce4-terminal is pretty nice.

---

### Post by GOROSSI on 2008-04-04
> **RedSquirrel said:**
> I agree with the recommendation of kerry_s to install the environment itself, not the desktop metapackage.

If you install the *-desktop metapackage, you get all the applications as well and you probably don't want all of that.

I don't use KDE, but I can say from my experience that setting up Xfce to your taste is really easy. It's just point & click.

Have a look at the xfce4 package information to see what it recommends for additional Xfce-specific packages (e.g., xfce4-terminal, xfce4-mixer, etc.). You can install those things too, if you like. xfce4-terminal is pretty nice.

> **kerry_s said:**
> 1. i recommend you just grab the environment->
sudo apt-get install xfce4
sudo apt-get install kde-core

2. of course it will, depends what's running. for instance the kde stuff is made to work together, when you run a kde item all the kde stuff starts as well. xfce4 is not bad, not much overhead there.

the real power of customizing is in the wm's, depending which 1, you can pick mostly everything you want to make up your setup.

for instance my laptops 450mhz 256mb ram, so i build it for low resource and speed. i use jwm for my wm, it's really light, but has alot of the desktop features, so i don't have to use extra programs for that. i use known light programs, such as rox-filer for file manager, leafpad for editor, etc...
i have full control of everything, i can even do the menu's my way.

most people tend to go for the *box's though, as jwm is a young wm, but i believe most of the lite distro's will switch to jwm because it has fantastic features yet is rock solid and lower on resources than the *box's.

Thirded, Installing the metapackage can cause no end of problems. It happened to me Years ago under the last Red Hat Desktop version.
 
had to do a clean install and Add KDE instead of GNOME under the command line

Op p's I got those quotes the wrong way round

---

### Post by CaesarLike on 2008-04-04
For what its worth, I recently installed the the full KDE desktop onto an Ubuntu install.  While KDE ran fine, I ended up with so many apps in my menus I could hardly find what I wanted.  Most confusing it was.  Best get just the desktop itself, and not all the apps.  Although some of the KDE apps are the best there is in linux, such as k3b.  As for the KDE desktop itself, I find its menu system too complicated and confusing.  Gnome is far easier to use I find.  I also had issues with the spash screen on bootup.  No matter whether I wanted to boot into Gnome or not, the KDE splash and login would always be shown.  Not a big problem, but an annoying one.

I also tried out Xubuntu and its XFCE desktop using a full Xubuntu install.  Its not a bad desktop, although I found it to have less features than the others.  But I would assume that if it is being put on top of an Ubuntu install, that this would be less a problem than installing Xubuntu itself.  The best XFCE app I found was Thunar file browser, it is way faster than Nautilus, but of course it has much less features as well.

---

### Post by Ozor Mox on 2008-04-05
Thanks for the replies everyone.

I installed the package 'xfce4' on my older PC and it worked fine, giving me the option to select it in GDM. When I logged in, I noticed that it was totally unconfigured, and it took me several minutes to work out that the little panel thing with one button on it was the equivalent of GNOME's top and bottom panels, and contains the system tray, open applications, menus etc. I got that set up in a matter of minutes and it's very fast.

> 2. of course it will, depends what's running. for instance the kde stuff is made to work together, when you run a kde item all the kde stuff starts as well. xfce4 is not bad, not much overhead there.

I realise if you run a KDE application in GNOME or XFCE it will need the libraries to be loaded and put an overhead on resources. I meant, if I log in to a XFCE session using only applications that run with XFCE, the fact that I have other desktop environments will not be a drain on resources except the obvious hard disk space? The idea is to keep GNOME, but be able to log in to XFCE for a faster environment.

> For what its worth, I recently installed the the full KDE desktop onto an Ubuntu install. While KDE ran fine, I ended up with so many apps in my menus I could hardly find what I wanted. Most confusing it was. Best get just the desktop itself, and not all the apps.

This is interesting. The package 'kde' was the one I was intending to install. I did notice it was half a gigabyte. Does it install way too much stuff? I would install 'kdebase' or 'kde-core' but I don't really know what these would give me or what their differences are. Anyone tried them? I know I can hide the additional menu items that I don't want.

---

