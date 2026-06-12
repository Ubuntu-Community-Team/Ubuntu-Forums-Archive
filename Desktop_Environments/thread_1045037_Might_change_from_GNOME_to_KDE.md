---
title: "Might change from GNOME to KDE"
date: 2009-01-20
forum: Desktop Environments
---

### Post by Fzang on 2009-01-20
I've always been a hardcore GNOME user and never tried any other enviroment, least the older versions of KDE because I couldn't stand the old oxygen icons...

So what changes if I jump from GNOME to KDE? Will any commands change? Will there be some software I can't use? What will it be?

---

### Post by x33a on 2009-01-20
most of the things will be same, except for the gui. 

there is no difference between the commands, for installed softwares or scripts. moreover, you can still use gtk+ apps on kde and vice-versa.

---

### Post by adamitj on 2009-01-20
As x33a said, you'll not have major problems in software compatibility. However, I tryed to move from Gnome to KDE last month, but with less than 2 or 3 days I returned to Gnome because KDE consumes too much resources of my "not-so-new" machine.

---

### Post by vmatherly on 2009-01-20
> **adamitj said:**
> As x33a said, you'll not have major problems in software compatibility. However, I tryed to move from Gnome to KDE last month, but with less than 2 or 3 days I returned to Gnome because KDE consumes too much resources of my "not-so-new" machine.

I agree :( KDE is much more of a resource hog than gnome. But its nothing compared to windows :-P. My laptop is an older machine it has a 1.8Ghz AMD CPU and 768MB of ram. It is usable but I definitely see a performance hit. Runs great on my desktop though.

Also once you switch some of your default apps will change. for instance instead of nautilus for a file manager you will be using Dolphin (im a big fan of Dolphin :-D). You can change these options in the system settings.

if your using Intrepid I would suggest testing out the newest 4.2 Release candidate. You can find out how to add the repo here:

[http://www.kubuntu.org/news/kde-4.2-rc1](http://www.kubuntu.org/news/kde-4.2-rc1)

4.2 has a lot of bug fixes and new features that make it much more usable than the current stable release. The official release of 4.2 is in 8 days so the RC is pretty stable at this point. It is defiantly worth the extra hassle.

---

### Post by x12796 on 2009-01-20
The easiest way I've found is if you're already running a fully functioning Ubuntu install, go into Synaptic and add Kubuntu Desktop.  This will install all of the KDE and KDE dependent programs. Then when you boot, at the login screen choose KDE under sessions and specify if it's only for this one time or perpetually.

---

### Post by lykwydchykyn on 2009-01-20
I would recommend not basing your impressions of KDE on 4.1 (Intrepid) or 4.0.  Get the 4.2 release candidate, or wait about another week or two for 4.2 final.  

4.x has been a do-over for KDE, so a lot of things are still maturing.

---

### Post by vmatherly on 2009-01-20
The method I use is:

```
sudo apt-get install kubuntu-desktop
```

This may not be the best way to do it if your just testing it out because it installs the whole kubuntu setup. I like this method because it installs all the kde apps, I like to test them out and just uninstall or disable later if I want to revert back to the gnome apps It will also ask you to chose KDM or GDM as you default display manager. I recommend keeping GDM to make it easyer to revert back. 

I have don this many times without much trouble. I did it when KDE4 came out didnt take long to realize that it wasn't ready for production use :(.I did it again when 4.1 beta was out and used it for a while before switching back to gnome. As soon as 4.2 beta was out I did it a third time :D. I think I may stick with it this time because it seems they fixed a lot of the things that drove me nuts with 4.1.

---

### Post by pansz on 2009-01-20
> **vmatherly said:**
> The method I use is:

```
sudo apt-get install kubuntu-desktop
```

 I like this method because it installs all the kde apps, 

No, kubuntu-desktop does *not* install all the kde apps, it just installs a small part of kde apps.

If you want to install all the kde apps: 
sudo apt-get install kde

---

### Post by pansz on 2009-01-20
> **Fzang said:**
> So what changes if I jump from GNOME to KDE? Will any commands change? Will there be some software I can't use? What will it be?

The biggest changes are the panel, the desktop, the system settings gui.

no command will change
no software you can't use

but this is not the right time to switch since kde4 isn't mature now, you may want to wait until ubuntu 9.04 or even ubuntu 10.04 to do the switch.

---

### Post by snova on 2009-01-20
> **pansz said:**
> No, kubuntu-desktop does *not* install all the kde apps, it just installs a small part of kde apps.

If you want to install all the kde apps: 
sudo apt-get install kde

kubuntu-desktop depends on kde, you'd actually get *more*. ;)

I do, however, recommend kde instead of kubuntu-desktop, because kubuntu-desktop drags in a lot of extras that are not necessarily desirable- a different bootsplash, display manager, and so on.

> **pansz said:**
> but this is not the right time to switch since kde4 isn't mature now, you may want to wait until ubuntu 9.04 or even ubuntu 10.04 to do the switch.

I disagree, I'm on 4.2 RC1, and it's awesome. :D

Personal opinion only, of course.

---

### Post by vmatherly on 2009-01-21
KDE 4,2 is awesome! It will be even better once more themes and customization options are available!

---

### Post by adamitj on 2009-01-21
What if he/she install only kde-core?

Install kubuntu-desktop from an existing Ubuntu installation really mess up with all gnome menus, filling them with all KDE applications. In my opinion, the best way is to install a fresh new Kubuntu version.

To avoid problems with actual Ubuntu (and my so loved Gnome), download VirtualBox and install it with a new guest Kubuntu installation.

You can get more information on how to set up VirtualBox here:
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by vmatherly on 2009-01-21
I tested KDE 4.2 out with vmware workstation first before I installed it on my main system. The only issue with doing this is that you don't get to test out the Visual effects.

---

