---
title: "Root doesn't work in GUI with Ubuntu and Kubuntu"
date: 2005-10-18
forum: Desktop Environments
---

### Post by fraqture on 2005-10-18
Hello,

In a (in retrospect) probably silly move I installed kubuntu-desktop and all related apps in Ubuntu so that I could run both Gnome and KDE (along with XFCE4, which I installed before kubuntu and worked just fine) in the same environment.

However, since I rebooted with the new KDE environment installed things started to mess up. I configured Ubuntu to enable logging in as root at the login screen (root login @ terminal still works) but now since Kubuntu has taken over my login screen I cannot do this anymore.

Also in Gnome the menu Adminisration > Login Screen Setup doesn't work anymore. Running this in a terminal window it says that it cannot find a certain configuration file. I wanted to use this to revert to my trusty old Gnome greeter theme but alas this doesn't work anymore now.

The system preferences menu in KDE allows you to go to Administrator mode but when I type in my password it just goes back to the way it was and I still can't change a ****.

Is there any way to reverse the changed Kubuntu made to my Ubuntu? I'm running ver 5.10.

---

### Post by Ampersand on 2005-10-18
If you open a terminal and type
```
sudo dpkg-reconfigure gdm
```, 
you can select between kdm and gdm as your login manager.

---

### Post by fraqture on 2005-10-18
[QUOTE=Ampersand]If you open a terminal and type
```
sudo dpkg-reconfigure gdm
```, 
you can select between kdm and gdm as your login manager.[/QUOTE]

Alright thanks, will try that when I get home :)

---

### Post by metoo on 2005-10-18
You can still stay with kdm:

The usual disclaimer: Don't login as root! blah, blah....

It's not a bug, it's a feature !
It's there to protect you against yourself and sometimes an annoyance.
So, from here you are on your own:

in /etc/kde3/kdm/kdmrc	'AllowRootLogin=true'

Take care!

---

