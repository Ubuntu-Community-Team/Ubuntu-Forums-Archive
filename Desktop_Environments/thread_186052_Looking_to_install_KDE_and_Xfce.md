---
title: "Looking to install KDE and Xfce"
date: 2006-06-01
forum: Desktop Environments
---

### Post by bruenig on 2006-06-01
I have the default ubuntu-desktop installed and I am wanting to be able to login to KDE and Xfce but I don't really want to clutter my menus with tons of applications from each desktop.

Is it possible to have GNOME, KDE, and Xfce installed and then choose which one I want to login to without having to deal with the default apps of all of them in the other environments?

Hopefully that's not too convoluted.

---

### Post by zhoux on 2006-06-01
i only know that you can install a "basic" install of KDE by doing
sudo apt-get install kde-core.
This install some kde files, but not alot of outside applications.

---

### Post by derrick1985 on 2006-06-01
[QUOTE=zhoux]i only know that you can install a "basic" install of KDE by doing
sudo apt-get install kde-core.
This install some kde files, but not alot of outside applications.[/QUOTE]

Yeah, and should be the same if you do a sudo apt-get install xfce

---

### Post by bruenig on 2006-06-01
zhoux, you were right about kde but for "basic" xfce, one must use sudo apt-get install xfce4

thanks

---

### Post by hoodwink on 2006-06-01
[QUOTE=bruenig]I have the default ubuntu-desktop installed and I am wanting to be able to login to KDE and Xfce but I don't really want to clutter my menus with tons of applications from each desktop.
[/QUOTE]
Just install kubuntu-desktop and xubuntu-desktop, then you can switch between the desired desktops as you like and/or run additional applications.

Just be aware that kubuntu-desktop is a sh**pot full of packages.

I'm running Kubuntu, but I installed ubuntu-desktop to have the GNOME apps available as needed.

---

### Post by TheHighChild on 2006-06-01
I hope this an appropriate thread for this.

Here's my story. I just did a dist-upgrade from breezy to dapper on my IBM T42. I rebooted and was unable to start my X because it could no longer find my mouse and keyboard drivers. I tried to apt-get them but they were already installed. I didn't care too much about this and just moved everything to my /home partiton and installed the newest Ubuntu release and moved everything back over to my new /home directory.

So, here I am, with Ubuntu installed (I got Ubuntu instead of Kubuntu, my bad) and I did the old sudo apt-get install kubuntu-desktop. It went fine and when I restarted my Xserver it appeared as though it was starting KDE (even the system boot shows the KDE splash) Everything is KDE even the login screen; However it just starts up Gnome. So this is my dilemma. 

Anyone know why I'm getting the KDE startup screens but ultimately getting the Gnome desktop? I am very grateful for any and all replies.

*EDIT*

Also, when I did the install of kubuntu-dekstop, it requested the default windowing manager, I selected KDE. After it started up with the Gnome desktop, I tried to stop Gnome with 
'sudo /etc/init.d/gdm stop'
It said gdm was stopped. I then tried
'sudo /etc/init.d/kdm start'
It said that KDE was already running. When I switched back to my Windowing failsafe terminal it was completely frozen. I left it for about 5 minutes and nothing. I couldn't even access my other failsafe terminals.

/Pretty odd. I just want to run KDE ;)

**EDIT**(again)

Ok, So it would seem I am just pretty stupid. I tried again and restarted my X. From the menu I was able to select KDE from the session type. Sooo...I am happy, KDE works and Gnome does too but why would it ask me for a default selection and no use it. I am used to this kind of thing with Linux windowing systems but what really surprises me is that it told me gdm was stopped and kdm was already running when I very clearly has a Gnome desktop. Also, why the Kubntu startup and splash screens if it's only going to use gdm?

I hope this doesn't sound like a flame, it isn't. I'm just surprised. Hopefully my follies will serve a higher purpose.

---

### Post by aysiu on 2006-06-01
Can people please stop telling others to *sudo apt-get install kubuntu-desktop*? Use *aptitude*, not *apt-get*. Otherwise, we'll keep getting questions about "How do I remove KDE?"

[http://www.psychocats.net/ubuntu/kde.html](http://www.psychocats.net/ubuntu/kde.html)
[http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

---

