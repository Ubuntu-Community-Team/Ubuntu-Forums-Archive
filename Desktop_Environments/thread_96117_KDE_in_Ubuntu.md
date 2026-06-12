---
title: "KDE in Ubuntu"
date: 2005-11-28
forum: Desktop Environments
---

### Post by Daminator on 2005-11-28
I'm interested in trying out KDE (or Kubuntu) and I have Ubuntu installed. Should I install KDE and how do you switch between them? I tried to add it in a previous install and all seemed to go fine, but I couldn't find a way to open up with KDE.

---

### Post by Sutekh on 2005-11-28
I say go for it.  Kubuntu is pretty rad.  I like having both GNOME and KDE.  If you use Synaptic, search for the **kubuntu-desktop** package.  If you want to use apt-get from the terminal
```

sudo apt-get install kubuntu-desktop

```
This installs everything for you (big download too).  You can choose to log into KDE from the log-in screen.  Click on "sessions" and choose KDE, then log in as usual.  You can select at that stage, which desktop to be your default.  To switch back, log out and choose GNOME in "sessions".

---

### Post by Daminator on 2005-11-28
Thanks Sutekh

I did this with my last install of Ubuntu, but didn't know how to get into it. I'd not seen anything about the 'sessions' thing.

So, is doing this exactly the same as installing Kubuntu? (wallpapers and all?) So I'll have both installed on there, switchable with no problems?

Sorry if I'm sounding over cautious but I've had to reinstall my entire system from scratch 3 times over the last couple of days and really don't want to break anything now that it's sorted.

---

### Post by sudharshan on 2005-11-28
correct me if am wrong but i sometimes while installing kubuntu or even kde  for that matter...some menu errors are obtained

---

### Post by LuxoDave on 2005-11-28
[QUOTE=Daminator]Thanks Sutekh

I did this with my last install of Ubuntu, but didn't know how to get into it. I'd not seen anything about the 'sessions' thing.

So, is doing this exactly the same as installing Kubuntu? (wallpapers and all?) So I'll have both installed on there, switchable with no problems?

Sorry if I'm sounding over cautious but I've had to reinstall my entire system from scratch 3 times over the last couple of days and really don't want to break anything now that it's sorted.[/QUOTE]

Yes, you will get all the default Kubuntu apps. I tried it the other night using apt-get and it worked perfectly. It does take a while to download.

---

### Post by Adrian on 2005-11-28
[QUOTE=Daminator]So I'll have both installed on there, switchable with no problems?[/QUOTE]

The Kubuntu programs will show up in your Gnome menus too, and some people don't like that. If you're one of them, take a look at the following HOWTO for a solution:
[http://www.ubuntuforums.org/showthread.php?t=59455](http://www.ubuntuforums.org/showthread.php?t=59455)

---

### Post by aysiu on 2005-11-28
[QUOTE=Daminator]
Sorry if I'm sounding over cautious but I've had to reinstall my entire system from scratch 3 times over the last couple of days and really don't want to break anything now that it's sorted.[/QUOTE] Actually, to be overly cautious, this is what you should do. Open up a terminal. Type in ```
sudo apt-get update
sudo apt-get install kubuntu-desktop
``` Before saying "yes" to installing it, highlight all the packages that are marked for installation; then, copy and paste that package list into a text file you save to your desktop.

That way, if you decide later on you don't want Kubuntu any more ("I just want it the way it was before"), you can type ```
sudo apt-get remove
``` and then paste in everything from that text file.

**Note**: simply typing ```
sudo apt-get remove kubuntu-deskop
``` will do *nothing*. Kubuntu-desktop is just a meta-package--it's not a real package that can be uninstalled. I'm amazed that more people don't warn folks about this.

If you don't do the copy and paste thing, I wrote [a HowTo](http://www.ubuntuforums.org/showthread.php?t=96048) (last night, actually) on removing the kubuntu-desktop packages; though, it's a bit imprecise, if you're already using some KDE applications.

---

### Post by Biased turkey on 2005-11-28
[QUOTE=sudharshan]correct me if am wrong but i sometimes while installing kubuntu or even kde  for that matter...some menu errors are obtained[/QUOTE]

I installed KDE with Ubuntu because I wanted to use Kdevelop for C++ programming. I had some X config files that were messed-up if I started Kdevelop from a gnome or xfce4 session.
So, I'm not the only one to have errors when using both Gnome and KDE.
I just reinstalled Ubuntu ( gnome only ) and switched from Kdevelop to Anjuta.

---

