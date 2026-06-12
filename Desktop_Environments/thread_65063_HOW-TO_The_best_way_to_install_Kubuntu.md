---
title: "HOW-TO: The best way to install Kubuntu"
date: 2005-09-12
forum: Desktop Environments
---

### Post by slooksterpsv on 2005-09-12
UPDATED FIRST POST, READ READ READ!!!
***IMPORTANT****
YOU CAN ONLY USE EITHER KDE OR GNOME ON MAC, EVEN WITH BOTH INSTALLED IF YOU BOOT INTO ONE YOU HAVE TO RESTART BEFORE YOU CAN USE ANOTHER ONE. ALTHOUGH, I HAVE NOT TRIED THIS WITH ANY OTHER WM'S LIKE ICEWM OR THAT, BUT YOU HAVE YOU RESTART IF YOU'VE USED GNOME AND WANT TO USE KDE AS YOUR SESSION. ALSO ALL MEDIA HAS TO BE REMOVED/EJECTED SUCH AS CD's USB DEVICES AND FIREWIRE DEVICES (THAT ARE STORAGE) BEFORE KDE WILL LET YOU LOG IN. THIS IS VERY VERY VITAL TO YOUR SUCCESS OF RUNNING KUBUNTU
***IMPORTANT****

Here's what you'll need:
Ubuntu for your type of system - Mac or PC
Kubuntu for your type of system - Mac or PC
1st:
If you don't have those, download both of them and burn them. If you don't know where to get them, how'd you find this forum? Just kidding its [http://www.kubuntu.org](http://www.kubuntu.org) and [http://www.ubuntu.com](http://www.ubuntu.com)
2nd:
Install Ubuntu - this helps to alleviate a lot of the Kubuntu problems.
After you install Ubuntu - update it.
3rd:
Install Kubuntu in Ubuntu - Open xterm and locate to /etc/apt then run sudo pico sources.list now # out all of the deb from [http://*web](http://*web) sites*/ this helps to speed up the installation a lot. CTRL+O to save, CTRL+X to exit.
4th:
Go into Synaptic under Gnome and search for all KDE. Install KDEBASE only, at first.
5th:
Next restart the computer and take out any media/media device that is on ur system -e.g. eject CDROM's, remove Firewire and USB storage devices.
6th:
Start KDE as you as a user.
7th:
Install juk under synaptic in KDE and restart - this takes like forever, I know
8th:
Login to Gnome and install the rest of the packages except KDM, Amarok, Amarok-arts, Konq-plugins, kscreensaver and kubuntu-default-settings.
9th:
Restart, again, after installing the rest of the packages. And ur finished
10th:
Post if it worked.

---

### Post by MrCheese on 2005-09-13
[QUOTE=slooksterpsv]Here's what you'll need:
Ubuntu for your type of system - Mac or PC
Kubuntu for your type of system - Mac or PC
1st:
If you don't have those, download both of them and burn them. If you don't know where to get them, how'd you find this forum? Just kidding its [http://www.kubuntu.org](http://www.kubuntu.org) and [http://www.ubuntu.com](http://www.ubuntu.com)
2nd:
Install Ubuntu - this helps to alleviate a lot of the Kubuntu problems.
After you install Ubuntu - update it.
3rd:
Install Kubuntu in Ubuntu - Open xterm and locate to /etc/apt then run sudo pico sources.list now # out all of the deb from [http://*web](http://*web) sites*/ this helps to speed up the installation a lot. CTRL+O to save, CTRL+X to exit.
4th:
Go into Synaptic under Gnome and search for all KDE. Install KDEBASE only, at first.
5th:
After you install KDEBASE and have started a session with KDE (log out and log in using session 3 which on mine is KDE, on urs it may be different) and its loaded up and works. REMOVED THIS PART DID NOT WORK ON MACS ONLY INSTALLING KDEBASE DID! - NOTE IF THIS DID NOT WORK AND YOU CAN'T OPEN A KDE SESSION UNINSTALL KDEBASE COMPLETELY AND RESINSTALL IT.
6th - Optional - HIGHLY RECOMMENDED FOR MAC TO ENSURE IT WORKS
Run updates for Kubuntu and Ubuntu.
7th - Optional
Post if it worked for you.

With Mac's there is a problem with... init_kndssnd or some thing like that. This makes it to where KDE will not load. So only base on Macs work. I have not tested to updates cause I'm on dial-up, but for x86 you can install everything right off the bat.[/QUOTE]


At least on my pc, after enabling the extra sources, all I did was to select all the KDE stuff, wait about 30 minutes then logged out & back in to kde, no problemo.

---

### Post by daller on 2005-09-13
Why install Ubuntu, and then Kubuntu?

I simply download a Kubuntu-iso, burn it, and install...

...Why all these troubles?

---

### Post by jnev on 2005-09-13
[QUOTE=daller]Why install Ubuntu, and then Kubuntu?

I simply download a Kubuntu-iso, burn it, and install...

...Why all these troubles?[/QUOTE]

...wondering the same thing...

---

### Post by slooksterpsv on 2005-09-13
[QUOTE=jnev]...wondering the same thing...[/QUOTE]
 Its mainly for Mac to be quite honest. It's easier to do it this way and see what does and doesn't work rather than install Kubuntu directly and have it not work - which is what happened to me.

---

### Post by philpot on 2005-09-13
[QUOTE=slooksterpsv]Here's what you'll need:
Ubuntu for your type of system - Mac or PC
Kubuntu for your type of system - Mac or PC
1st:
If you don't have those, download both of them and burn them. If you don't know where to get them, how'd you find this forum? Just kidding its [http://www.kubuntu.org](http://www.kubuntu.org) and [http://www.ubuntu.com](http://www.ubuntu.com)
2nd:
Install Ubuntu - this helps to alleviate a lot of the Kubuntu problems.
After you install Ubuntu - update it.
3rd:
Install Kubuntu in Ubuntu - Open xterm and locate to /etc/apt then run sudo pico sources.list now # out all of the deb from [http://*web](http://*web) sites*/ this helps to speed up the installation a lot. CTRL+O to save, CTRL+X to exit.
4th:
Go into Synaptic under Gnome and search for all KDE. Install KDEBASE only, at first.
5th:
After you install KDEBASE and have started a session with KDE (log out and log in using session 3 which on mine is KDE, on urs it may be different) and its loaded up and works. REMOVED THIS PART DID NOT WORK ON MACS ONLY INSTALLING KDEBASE DID! - NOTE IF THIS DID NOT WORK AND YOU CAN'T OPEN A KDE SESSION UNINSTALL KDEBASE COMPLETELY AND RESINSTALL IT.
6th - Optional - HIGHLY RECOMMENDED FOR MAC TO ENSURE IT WORKS
Run updates for Kubuntu and Ubuntu.
7th - Optional
Post if it worked for you.

With Mac's there is a problem with... init_kndssnd or some thing like that. This makes it to where KDE will not load. So only base on Macs work. I have not tested to updates cause I'm on dial-up, but for x86 you can install everything right off the bat.[/QUOTE]
 I tried to install Ubuntu on a Mac without success. Kubuntu installed fine, first time.

---

### Post by mlomker on 2005-09-13
[QUOTE=daller]...Why all these troubles?[/QUOTE]

Many people run gnome applications, such as Firefox and Synaptic anyway.  You almost end up installing all of Ubuntu to make those applications run...it almost doesn't matter.

---

### Post by slooksterpsv on 2005-09-14
[QUOTE=mlomker]Many people run gnome applications, such as Firefox and Synaptic anyway.  You almost end up installing all of Ubuntu to make those applications run...it almost doesn't matter.[/QUOTE]
 Well things are working for me even with KDM installed. I guess its just a media problem where if you have attached media trying to connect to KDE it won't work. I have tons of other WM's too, Fluxbox, Openbox, Blackbox, Waimea, etc.

---

