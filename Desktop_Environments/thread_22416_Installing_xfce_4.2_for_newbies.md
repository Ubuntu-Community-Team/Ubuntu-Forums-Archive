---
title: "Installing xfce 4.2 for newbies?"
date: 2005-03-27
forum: Desktop Environments
---

### Post by BlackHawk on 2005-03-27
Hello all.

Installed Hedgehog 5.04 yesterday without much for problems.  Managed to get my dialup working thanks to whomever did the DialupModemHowto. =D> 

Have seen xfce at work on my friends computer and would like to install it.  Problem being, after reading everything I can find, I'm clueless. :-( 

Could anyone please tell me how to grab this little speedster and install it on my system?  Or point me in the direction of a tutorial I very well might have missed?

Thank you...

---

### Post by taygan on 2005-03-27
xfce 4.0 is in the ubuntu universe repository - do a forum search for repositories if you need to add universe and/or multiverse to apt/synaptic.

xfce 4.2.1.1 unofficial repository can be added, although it's not specifically for ubuntu, I've added it and with some extra tweaks have it up and running:

check out [www.xfce.org](www.xfce.org) download section for more information.

or, add these lines to your apt sources.list (can be done through synaptic>settings>repositories, although sometimes I have to reboot to get synaptic to reset the repositories.)

```
deb http://www.os-works.com/debian testing main
deb-src http://www.os-works.com/debian testing main
```

or, you can use the binary installer from xfce, although I prefer using the debs so I can add and remove what I need.


**  EDIT: 4.2.1.1 is now in the UNIVERSE repositories.  You don't need the os-cilliation repositories.  ** xfce4 is what you want. **

---

### Post by DJ_Max on 2005-03-27
I'm installing the latest version (4.2.1) with the binary installer [http://www.os-cillation.com/article.php?sid=43](http://www.os-cillation.com/article.php?sid=43)

It's simple. I'll let you know how it goes.

EDIT:
Install went find, except for the uninstaller, which didn't register. Everything else is fine so far.

---

### Post by taygan on 2005-04-12
Ubuntu now has xfce 3.8 as the "xfce" metapackage and xfce 4.2 as the "xfce4" metapackage in the universe repository.  Most folks will want the xfce4 meta package.

---

### Post by Psquared on 2005-04-18
I used the binary installer and it worked fine -- except for one thing. No panel at the bottom. The menus are there, but I like the bottom panel. I've tried adjusting the settings, but unless there's something I'm not seeing I can't get it show.

BTW, I am using Warty. Could that be the problem?

---

### Post by kelvinq on 2005-04-19
I've been using xfce for a few days now and no problems at all. Everything was fast and speedy.

I installed xcfe using Synaptic. You don't even have to deal with the installer or answer any questions. It's a brainless installation process. :)

---

### Post by Psquared on 2005-04-19
I went to the os-cillation web site and read their forum. Apparently sometimes the panel does not start the first time after installation. I opened a terminal and ran the command xfce4-panel and it popped up. 

The menu structure is a bit confusing and messy. They need to work on that. I've got OpenOffice in two locations and the Debian entry is blank. I can't get rid of it either. Also, customizing the wallpaper, windows and icon themes is all done by separate menu items none of which say anything about themes or backgrounds.

Finally, if I could reorganize and rename the menu to my liking I'd be perfectly happy.

---

### Post by GOwin on 2005-04-20
I've managed to install and use xfce but while tinkering around managed to make the screen unreadable during XFCE sessions).

Using gnome works ok. How do i fix this?

I tried dpkg-reconfigure but there weren't any changes.

---

### Post by zagor on 2005-04-20
I'll add another question to this thread: I've installed xfce 3.8 a few weeks ago.
Now I'd like to remove it and substitute with xfce4.

Is there an automatic way to remove ALL comonents of xfce?
Maybe removing some core packages which automatically removes the now useless packages?

Thanks

---

### Post by Psquared on 2005-04-20
I believe you use the purge command with apt-get or aptitude. That will remove all the components and configuration files.

sudo apt-get purge xfce

Try that.

---

### Post by siebzehn on 2005-04-20
[QUOTE=Psquared]I believe you use the purge command with apt-get or aptitude. That will remove all the components and configuration files.

sudo apt-get purge xfce

Try that.[/QUOTE]


I think it's supposed to be    "sudo apt-get remove --purge xfce"

---

