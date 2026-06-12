---
title: "Removed Unity, updates want to reinstall it"
date: 2012-09-12
forum: Desktop Environments
---

### Post by 73ckn797 on 2012-09-12
I have removed the Unity DE using this command:
```
sudo apt-get remove unity unity-2d-places unity-2d unity-2d-panel unity-2d-spread unity-asset-pool unity-services unity-lens-files unity-lens-music unity-lens-applications gir1.2-unity-4.0 unity-common indicator-sound indicator-power indicator-appmenu libindicator7 indicator-application evolution-indicator indicator-datetime indicator-messages libnux-2.0-0 nux-tools
```
I have been doing this since the release of 12.04 and everything was smooth.


The latest software updates, on 2 computers, tells me all updates cannot be installed and would I prefer a partial upgrade. The partial upgrade is the Unity DE. If I decline the partial upgrade the remaining updates cannot be selected. I went ahead and allowed the upgrade and the other updates now install. I again have run the remove procedure and no longer have Unity and am back to Gnome 3.

I know I could just leave Unity as is and not use it. I do not have a disk space problem.

Anyone having this happen?

---

### Post by jerrrys on 2012-09-12
I wonder if this would solve your problem.

[http://linux-software-news-tutorials.blogspot.com.es/2012/04/totally-remove-unity-from-ubuntu-1204.html?utm_source=twitterfeed&utm_medium=twitter](http://linux-software-news-tutorials.blogspot.com.es/2012/04/totally-remove-unity-from-ubuntu-1204.html?utm_source=twitterfeed&utm_medium=twitter)

---

### Post by 73ckn797 on 2012-09-14
> **jerrrys said:**
> I wonder if this would solve your problem.

[http://linux-software-news-tutorials.blogspot.com.es/2012/04/totally-remove-unity-from-ubuntu-1204.html?utm_source=twitterfeed&utm_medium=twitter](http://linux-software-news-tutorials.blogspot.com.es/2012/04/totally-remove-unity-from-ubuntu-1204.html?utm_source=twitterfeed&utm_medium=twitter)

Thanks. I see there is more removed with the commands than what I was using. I have performed the procedure and had no problems. Checked for updates and for now no unity components were listed.

I will give it a few days and see what happens.

---

### Post by 73ckn797 on 2012-09-15
The commands given do not stop the system from wanting to perform a partial upgrade back to Unity. Here are some attached screenshots.
It will not be any big deal to have Unity installed but run in fallback session.

---

### Post by jerrrys on 2012-09-15
Do you have the package "ubuntu-desktop" still loaded?  Need to do a little research on it, but as I recall that's a mega package that would want to install Unity and can be safely removed without any loss of packages.  May someone else will come along and verify this.

---

### Post by AlanR8 on 2012-09-15
Why did you want to remove Unity?

---

### Post by 73ckn797 on 2012-09-16
> **jerrrys said:**
> Do you have the package "ubuntu-desktop" still loaded?  Need to do a little research on it, but as I recall that's a mega package that would want to install Unity and can be safely removed without any loss of packages.  May someone else will come along and verify this.
No, it is not installed. There are no Unity packages installed at all at this point either.

---

### Post by 73ckn797 on 2012-09-16
> **AlanR8 said:**
> Why did you want to remove Unity?
I do not care for it so I removed it. Not a critique of it but just a personal preference. I have considered installing Gnome 3 but have not completed my research of whether I could live with that for the purposes I have. That is a topic for another thread.

---

### Post by CaptainMark on 2012-09-16
You can install gnome-shell alongside unity, removing unity can cause all sorts of problems unless you know exactly what you are doing, so I would install gnome-shell and just leave unity as it is, it wont use up any system resources if you aren't using it so just select gnome-shell at login and you'll have no problem, use this code to do that```
sudo apt-get update; sudo apt-get -y dselect-upgrade; sudo apt-get install gnome-shell
```

---

### Post by cwsnyder on 2012-09-16
OK, I'm confused.  What DE are you using at present? KDE? Xfce? JWM? Awesome?

I have never had a problem running Xfce/Xubuntu desktop after installing from an Ubuntu disk, then installing xubuntu-desktop from the CLI and removing Unity.

---

### Post by vexorian on 2012-09-16
Remove ubuntu-desktop. It is merely a meta-package and the most likely cultprit of this thing.

---

### Post by 73ckn797 on 2012-09-16
> **cwsnyder said:**
> OK, I'm confused.  What DE are you using at present? KDE? Xfce? JWM? Awesome?

I have never had a problem running Xfce/Xubuntu desktop after installing from an Ubuntu disk, then installing xubuntu-desktop from the CLI and removing Unity.
My avatar/info shows I am running Ubuntu 12.04, which is why I have it there.

---

### Post by 73ckn797 on 2012-09-16
> **vexorian said:**
> Remove ubuntu-desktop. It is merely a meta-package and the most likely cultprit of this thing.
That has already been suggested and replied to.

---

### Post by 73ckn797 on 2012-09-16
> **CaptainMark said:**
> You can install gnome-shell alongside unity, removing unity can cause all sorts of problems unless you know exactly what you are doing, so I would install gnome-shell and just leave unity as it is, it wont use up any system resources if you aren't using it so just select gnome-shell at login and you'll have no problem, use this code to do that```
sudo apt-get update; sudo apt-get -y dselect-upgrade; sudo apt-get install gnome-shell
```
Gnome-shell is already installed.

> **CaptainMark said:**
> sudo apt-get -y dselect-upgrade

I have not run this command. Would that lock out the ability of the Update Manager to request the re-installation of the Unity packages, the "partial upgrade?"

---

### Post by CaptainMark on 2012-09-16
'dselect-upgrade' is like the beefed up version of 'upgrade', it will update all packages just like 'upgrade' but also has the ability to install additional packages if an existing package needs a new dependency. It in effect will run a partial upgrade.

Partial upgrades are a messy situation where one package has been removed but another package that is installed must have the first one installed in order to function, you need to try and get out of the partial upgrade loop as soon as possible to avoid getting deeper into '[dependency hell]("http://en.wikipedia.org/wiki/Dependency_hell")'

the -y flag just assumes the answer to any yes/no questions as yes

EDIT: just to reiterate this is not something you have done wrong, you should be able to remove any package and apt-get should clear up any dependency conflicts but something obviously went wrong

---

### Post by 73ckn797 on 2012-09-16
> **CaptainMark said:**
> 'dselect-upgrade' is like the beefed up version of 'upgrade', it will update all packages just like 'upgrade' but also has the ability to install additional packages if an existing package needs a new dependency. It in effect will run a partial upgrade.

Partial upgrades are a messy situation where one package has been removed but another package that is installed must have the first one installed in order to function, you need to try and get out of the partial upgrade loop as soon as possible to avoid getting deeper into '[dependency hell]("http://en.wikipedia.org/wiki/Dependency_hell")'

the -y flag just assumes the answer to any yes/no questions as yes

EDIT: just to reiterate this is not something you have done wrong, you should be able to remove any package and apt-get should clear up any dependency conflicts but something obviously went wrong

Thanks for the info. I will monitor what happens on the computer in question, a desktop. My laptop still has Unity but I am running Gnome in fall back session and also have Gnome shell installed. The issue has not re-occurred since putting Unity back on the laptop.

---

