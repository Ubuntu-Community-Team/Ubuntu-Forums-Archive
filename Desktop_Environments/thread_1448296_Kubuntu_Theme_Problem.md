---
title: "Kubuntu Theme Problem"
date: 2010-04-06
forum: Desktop Environments
---

### Post by Nyxielle on 2010-04-06
I used to have Ubuntu and I loved it but then my laptop broke and I got a new one that ran vista and I couldn't really be bothered and didn't really have the time to download and install a new OS.

Anyway, recently I'd had just about enough of M$ and decided to get linux back. Only this time I decided I'd try KDE.

After a clean install of Kubuntu I decided to download some themes to make my desktop look all pretty ^^

I was having some difficulties figuring out how exactly to install these themes, it seemed so much easier with Gnome
Next time I booted up my system I'd get to the login bit, type in my password and then all I'd see would be the desktop wallpaper, nothing else and I'd hear the login noise
I tried rebooting and that didn't change anything
I ended up clean installing Kubuntu AGAIN
...and proceeded to try again at getting a new theme on this
big mistake.
I ended up right back with the same problem.
Again I reinstalled Kubuntu

But I really want some new themes, but I'm kind of fed up with reinstalling everything all over again if nothing's going to work anyways. I don't want to break anything again.

So if anyone could help me please
How do I get a new theme on this without breaking it?
If I end up with the same problem again is there anyway to fix it without having to reinstall Kubuntu?

Also, When I had Ubuntu if I logged out it took me back to the login screen
On Kubuntu, when I log out it takes me to command line, is there anyway to get it so that when I log out I see the login screen.
I know it's possible to still login and everything from command line but I'd prefer to have the GUI.

---

### Post by Old *ix Geek on 2010-04-26
I'm surprised no one's answered after so long! :confused:

It sounds like you're missing some of the components for a true 'complete' install of Kubuntu.  Use Synaptic to install them.

**System > Synaptic Package Manager**

In the 'Quick search' box at the top, enter **kde**. From the LONG list of files that appears, concentrate on names that begin with 'kde.' Go through and select everything that sounds like it's necessary for a complete installation, such as 'kdebase' and 'kdebase-runtime.'  Read the descriptions to help figure it out. While you're there install icons, themes, etc. You can ignore anything that ends in **-dbg** and **-devel**, plus obvious things you don't care about, like 'Kashubian internationalized (i18n) files for KDevelop and KDEWebDev' :D

See if that solves your problem. If not, post again!

---

### Post by Zorael on 2010-04-27
Whenever the panel and widgets don't draw (and you end up with an empty desktop or a black screen), this usually indicates that plasma is missing or that it crashed for some reason. It can end up missing if you try to do an upgrade (perhaps to KDE 4.4 from the kubuntu ppas) and it gets botched somehow.

What you want to do is to first make sure you have all the packages you need. This requires a net connection. Hit Alt+F2 to get the run menu to pop up and start Konsole (by typing 'konsole' or 'terminal') from there.
```
$ sudo aptitude update
$ sudo aptitude full-upgrade plasma-desktop+
```

Now either log out by merely typing 'log out' in the run menu, or reboot your computer, or try to start plasma manually and see what it says.
```
$ plasma-desktop
```

(As for themes, in my experience they should be fairly easy to install if you use the Get Hot New Stuff feature when browsing them in System Settings.)

---

### Post by Falc7 on 2010-04-27
Easiest way i find to get new themes, is system settings-> appearance -> workspace -> get new themes

---

### Post by Old *ix Geek on 2010-04-27
> **Falc7 said:**
> Easiest way i find to get new themes, is system settings-> appearance -> workspace -> get new themesThere's no such choice on Kubuntu 9.10. :confused:

---

### Post by Zorael on 2010-04-27
> **Old *ix Geek said:**
> There's no such choice on Kubuntu 9.10. :confused:
It moved there in 4.4.

In 4.3 I think you'll find it in System Settings -> Advanced tab -> Desktop Theme Details, or something like that.

---

