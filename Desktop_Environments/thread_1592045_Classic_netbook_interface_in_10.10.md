---
title: "Classic netbook interface in 10.10?"
date: 2010-10-10
forum: Desktop Environments
---

### Post by jxjl on 2010-10-10
I've downloaded new ubuntu, but I found out, that old classic netbook launcher was removed from repos. Is there any way, how to install it in 10.10 (PPA or updated source)?

---

### Post by kerry_s on 2010-10-10
the 2d version is still there in the repos, you can use that.

---

### Post by webdebbyjoss on 2010-10-12
Hi, I have a same problem. 

There is no any package called "netbook-launcher" in repos anymore. 
I use Ubuntu 10.10 Desktop Edition.

My aim was to build the same interface as it was in Ubuntu 10.04 UNR

So I tried to install:

1. "Window Picker" applet that has also window title-bar functionality.
2. "Maximus" daemon to turn off windows decoration on windows maximization
3. "Go Home Applet" to show a desktop (netbook-launcher menu)

so the last step is to install netbook launcher

But I'm not able to find "netbook-launcher" package anymore in repos. 
Where can I find it, without building from the sources available on Launchpad?

---

### Post by kerry_s on 2010-10-12
> **webdebbyjoss said:**
> Hi, I have a same problem. 

There is no any package called "netbook-launcher" in repos anymore. 
I use Ubuntu 10.10 Desktop Edition.

My aim was to build the same interface as it was in Ubuntu 10.04 UNR

So I tried to install:

1. "Window Picker" applet that has also window title-bar functionality.
2. "Maximus" daemon to turn off windows decoration on windows maximization
3. "Go Home Applet" to show a desktop (netbook-launcher menu)

so the last step is to install netbook launcher

But I'm not able to find "netbook-launcher" package anymore in repos. 
Where can I find it, without building from the sources available on Launchpad?


netbook-launcher-efl is the 2d version.

---

### Post by chamm on 2010-10-12
I, too, don't care for the Unity interface. I agree with the principles behind making it the default interface for UNR 10.10, but I wish they'd kept the old interface at least in the repos. Despite what I keep hearing, Unity is S L O W on my netbook. Much slower than any of the other interfaces I've tried out.

I set up the 2D version as per the instructions above, however, I can't seem to launch more than one instance of an application. (For instance, if I wanted to open two terminals, which I do often.) If I could get around this limitation, that would probably be my interface of choice. It's pretty snappy, and doesn't look bad at all. Any ideas how I could make this happen?

---

### Post by kerry_s on 2010-10-12
> **chamm said:**
> I, too, don't care for the Unity interface. I agree with the principles behind making it the default interface for UNR 10.10, but I wish they'd kept the old interface at least in the repos. Despite what I keep hearing, Unity is S L O W on my netbook. Much slower than any of the other interfaces I've tried out.

I set up the 2D version as per the instructions above, however, I can't seem to launch more than one instance of an application. (For instance, if I wanted to open two terminals, which I do often.) If I could get around this limitation, that would probably be my interface of choice. It's pretty snappy, and doesn't look bad at all. Any ideas how I could make this happen?

in gconf-editor, there should be a setting for that.

---

### Post by chamm on 2010-10-14
> **kerry_s said:**
> in gconf-editor, there should be a setting for that.
I've given it my best effort, but I can't seem to figure out what setting in gconf-editor will allow this. Could you please point me in a direction? Thanks in advance!

---

### Post by arinya on 2010-10-17
Similiarly, I have removed all related netbook, such unity, mutter, etc. and returned back to normal desktop session for the UNITY is really SLOW.

Indeed, I am also dislike netbook-launcher, a traditional gnome menu applet is far more better.

Maximus is great and the only one real important thing for small screen.

So, Main Menu + Show Desktop + window-picker-applet + Notification Area + Indictor Applet + Clock is all one needed. all these applets are placed at the top panel.

In this way, I changed ubuntu-netbook-edition to ubuntu-desktop-edition with a classical UNR-like interface.

---

### Post by CryNGRoad on 2011-02-06
[QUOTE="chamm"]...I can't seem to launch more than one instance of an application. (For  instance, if I wanted to open two terminals, which I do often.) If I  could get around this limitation, that would probably be my interface of  choice. It's pretty snappy, and doesn't look bad at all. Any ideas how I  could make this happen?[/QUOTE]
To open more than one terminal in netbook-launcher-efl, in the terminal's **File** menu, click **Open Terminal** *Shift+Ctrl+N* :)

Many applications have a similar menu item (e.g. Firefox, Nautilus, etc).

---

