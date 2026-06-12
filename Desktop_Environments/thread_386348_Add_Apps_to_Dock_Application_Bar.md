---
title: "Add Apps to Dock Application Bar"
date: 2007-03-16
forum: Desktop Environments
---

### Post by Apoorv on 2007-03-16
How am I supposed to add applications to the Dock Application Bar??
Nothing happens when I right click on it, and I can only change it's position from the 'Configure KDE Panel' dialog. I want to add apps to the dock. How do I do it? Drag 'n' drop doesn't work too.

---

### Post by Apoorv on 2007-03-16
Or is there some other method by which I can create a dock in KDE???

---

### Post by barney_1 on 2007-03-16
Edit:  completely botched it on that solution.  Sorry but I'm no help to you.

---

### Post by ZERO_SHIFT on 2007-03-17
Okay, you can either install Gdesklets and install a launcher(aka dock) from thereor you might want to install the fancy Kiba dock through their website.

---

### Post by Apoorv on 2007-03-17
But what's wrong with the Kicker Dosk Application Bar?? How do you guys add shortcuts to it?

---

### Post by Apoorv on 2007-03-17
Bump.

---

### Post by barney_1 on 2007-03-19
I don't know what's wrong with your menu bar.  When I right-click mine I get the choice of "panel menu" and inside of that menu I can choose "add applet to panel", "add application to panel", etc.

---

### Post by Apoorv on 2007-03-21
I can add shortcuts to the menu bar, but not the DOCK APPLICATION BAR! 

[http://docs.kde.org/stable/en/kdebase/kicker/dock-application-bar-extension.html](http://docs.kde.org/stable/en/kdebase/kicker/dock-application-bar-extension.html)

^^^
This Dock Application bar, this is a panel extension, I want to add shortcuts for programs to this. I get this by 

Right click on main panel >> Add panel >> Add Dock Application Bar.

All I can configure in this bar is it's position, that too by right clicking on the main panel and configure (or something like that). I get a 'Configure KDE Panel' dialog, and I can configure only the position of the Dock Application Bar from here.

---

### Post by Apoorv on 2007-03-22
Bump.

---

### Post by theCoder on 2007-03-24
This 'Dock Application' bar is specifically for people who use WindowMaker applications ([http://windowmaker.info]("http://windowmaker.info")). There are several applications written for that window manager that don't directly integrate with KDE, and were meant to be used with WindowMaker's dock. If you do not use any of those applications (if you do not know what I am talking about, then you don't) then the Dock Application bar is of no use to you.

Here is a 6 year old article (no it hasn't changed much since then) describing its use: [http://www.linuxjournal.com/article/4728]("http://www.linuxjournal.com/article/4728")

I am not an Ubuntu user, atm, so I can't confirm if it comes with WindowMaker or not, but I just registered here for the sole purpose of answering you (since no one else had in several days). Regardless, I am an avid KDE user, and used WindowMaker back in the day before KDE 1.x had become mature.

Some applications that mimic the MacOS X dock in KDE are Kooldock, Ksmoothdock, and Kxdocker. Check apt-get to see if you have any avalable for Ubunto or google for them to compile and install yourself.

Best of luck

---

### Post by rebegin on 2007-05-03
installing debian packages worked for me:
[http://packages.debian.org/testing/x11/kxdocker](http://packages.debian.org/testing/x11/kxdocker)
[http://packages.debian.org/testing/x11/kxdocker-data](http://packages.debian.org/testing/x11/kxdocker-data)

---

