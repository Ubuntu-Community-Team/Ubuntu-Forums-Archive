---
title: "Xubuntu desktop on ubuntu 11.04"
date: 2011-07-31
forum: Desktop Environments
---

### Post by moorhead98 on 2011-07-31
I have Ubuntu 11.04 on a laptop. I want to try out Xubuntu, but when I try and download it in synaptic, it says that it would have to get rid of Ubuntu desktop. 
Is that a bug, or did I do something to make it like that? And is it possible get xubuntu desktop without removing ubuntu desktop?
I'm up for anything

---

### Post by George W. Tush on 2011-07-31
I did not have that experience at all.  Unity was a bug fest and I hated it.  So I added the Xubuntu interface.  All the 'buntus are the same, I believe.  The difference is with the interface.  gnome is one interface.  Unity is another.  xfce is a third.  They don't run at the same time and they don't compete.  They just each interact with the underlying 'buntu.  When I boot, xubuntu is a choice, exactly as as ubuntu, ubuntu classic, etc., is currently a choice with 11.04.

You might try looking here.  And good luck!

[http://www.xubuntu.org/getubuntu](http://www.xubuntu.org/getubuntu)

---

### Post by moorhead98 on 2011-07-31
> **George W. Tush said:**
> I did not have that experience at all.  Unity was a bug fest and I hated it.  So I added the Xubuntu interface.  All the 'buntus are the same, I believe.  The difference is with the interface.  gnome is one interface.  Unity is another.  xfce is a third.  They don't run at the same time and they don't compete.  They just each interact with the underlying 'buntu.  When I boot, xubuntu is a choice, exactly as as ubuntu, ubuntu classic, etc., is currently a choice with 11.04.

You might try looking here.  And good luck!

[http://www.xubuntu.org/getubuntu](http://www.xubuntu.org/getubuntu)

Look at the picture. I circled what is concerning me. 
I do not want to get rid of ubuntu desktop. or notify osd (under one of the circles) 
So without getting rid of what i want to keep, is it possible to get xubuntu?

---

### Post by haresear on 2011-07-31
I was skeptical of this behavior because I have installed kde-desktop on my Ubuntu 11.04 and it did not uninstall ubuntu-desktop, but I tried it on my ubuntu/kubuntu 11.04 system, and you are right! When I marked xubuntu-desktop for install, synaptic wants to uninstall ubuntu-desktop. I have no idea why it does this. As an experiment, I tried to install ubuntu-desktop on a (different) Xubuntu 11.04 system, and sure enough it wants to uninstall xubuntu-desktop. So it does seem consistent -- apparently xubuntu and ubuntu desktops can't coexist. Just out of curiosity I tried to install the meta package "xfce" to Ubuntu 11.04, and it did not want to uninstall anything. The description of the xfce meta-package says that it would allow you run an xfce desktop, so that might be a solution for you. You would probably be missing the Xubuntu themes, but the essential components should be there.

PS- I have noticed that Xubuntu uses some gnome libraries, so perhaps that is why it won't coexist with gnome-based Ubuntu, e.g. maybe Xubuntu is using an older gnome library that conflicts with a newer library used by Ubuntu.

---

### Post by Winelord on 2011-08-01
Hi, you can install Xubuntu without removing Ubuntu.

The message you get in Synaptic is a bit confusing- it won't actually remove the Ubuntu desktop environment, it just removes  the (no longer required) installer instructions.

Go ahead- it won't cause any problems. I've experimented with using Xubuntu with Ubuntu, & Kubuntu with Ubuntu- everything works fine.

Once you've installed Kubuntu, you select which *buntu you want to use via the login screen.

---

### Post by XubuRoxMySox on 2011-08-01
**[COLOR="Blue"]xubuntu-desktop[/COLOR]** is what they call a *metapackage*. A "bundle," so to speak. The same is true for ubuntu-desktop, kubuntu-desktop, and lubuntu-desktop.

Xubuntu-desktop is different from just installing Xfce on top of Ubuntu, though! Xubuntu is Xfce *configured* for an Ubuntu system and an "ordinary user." It also includes lighter-weight applications! **[COLOR="Blue"]Xubuntu-desktop[/COLOR]**, for example, *includes* the ultralight Abiword word processor and Gnumeric spreadsheet app because they're so very much lighter and less resource-hungry than the Ubuntu default, LibreOffice. It'll also bring in the Parole media player and a few other lighter apps to try.

If you have plenty of room on your hard drive, try them all! It's pretty fun to get to know them.

The only thing is that when you want to try one you've just installed, you have to log out, and log in again choosing "Xubuntu" for that **session**. That will log you into a custom-made honest-to-goodness Xubuntu desktop experience.

I love my Xubu! I call it, *"Debian for Human Beings."* :D

---

### Post by moorhead98 on 2011-08-01
> **haresear said:**
> I was skeptical of this behavior because I have installed kde-desktop on my Ubuntu 11.04 and it did not uninstall ubuntu-desktop, but I tried it on my ubuntu/kubuntu 11.04 system, and you are right! When I marked xubuntu-desktop for install, synaptic wants to uninstall ubuntu-desktop. I have no idea why it does this. As an experiment, I tried to install ubuntu-desktop on a (different) Xubuntu 11.04 system, and sure enough it wants to uninstall xubuntu-desktop. So it does seem consistent -- apparently xubuntu and ubuntu desktops can't coexist. Just out of curiosity I tried to install the meta package "xfce" to Ubuntu 11.04, and it did not want to uninstall anything. The description of the xfce meta-package says that it would allow you run an xfce desktop, so that might be a solution for you. You would probably be missing the Xubuntu themes, but the essential components should be there.

PS- I have noticed that Xubuntu uses some gnome libraries, so perhaps that is why it won't coexist with gnome-based Ubuntu, e.g. maybe Xubuntu is using an older gnome library that conflicts with a newer library used by Ubuntu.

Or maybe it uses the newest gnome 3 libraries, that would break unity?

---

### Post by moorhead98 on 2011-08-01
> **Winelord said:**
> Hi, you can install Xubuntu without removing Ubuntu.

The message you get in Synaptic is a bit confusing- it won't actually remove the Ubuntu desktop environment, it just removes  the (no longer required) installer instructions.

Go ahead- it won't cause any problems. I've experimented with using Xubuntu with Ubuntu, & Kubuntu with Ubuntu- everything works fine.

Once you've installed Kubuntu, you select which *buntu you want to use via the login screen.

So i can install xubuntu-desktop, and it wont uninstall Ubuntu-desktop?
I've installed/uninstalled Kubuntu and Lubuntu without any bizarre warnings, so this one is a little troubling, and I want to make sure that i can do it without breaking something
Also, have you installed xubuntu-desktop on ubuntu **_11.04_**? Could be that xubuntu uses some gnome libraries that are from gnome 3 and would break Ubuntu desktop on 11.04?

---

### Post by moorhead98 on 2011-08-03
It also said that it would remove notify-osd.
Whats up with that?

---

### Post by Winelord on 2011-08-04
> **moorhead98 said:**
> So i can install xubuntu-desktop, and it wont uninstall Ubuntu-desktop?
I've installed/uninstalled Kubuntu and Lubuntu without any bizarre warnings, so this one is a little troubling, and I want to make sure that i can do it without breaking something
Also, have you installed xubuntu-desktop on ubuntu **_11.04_**? Could be that xubuntu uses some gnome libraries that are from gnome 3 and would break Ubuntu desktop on 11.04?

It won't uninstall Ubuntu, they'll be there side-by-side, just like your Kubuntu/Lubuntu installation. The principle is just the same.

Personally, I haven't used it with v.11.04, but it does work. There's an illustrated guide here: [http://www.psychocats.net/ubuntu/xfce]("http://www.psychocats.net/ubuntu/xfce"). Hope this helps.

11.04 is based on Gnome 2. At this point in time, Gnome 3 is considered highly unstable, and would cause problems, if you've manually downloaded it.

---

### Post by Winelord on 2011-08-04
Notify OSD is a daemon (background process) that displays notification bubbles (eg. network connections, battery power). It should remain in Ubuntu.

If for any reason it is not in Xubuntu, just go into Synaptic Package Manager and search for notify osd. If required, just select & install it.

AFAIK, Xubuntu just uses a slightly different notifier by default.

---

### Post by haresear on 2011-08-04
On my Xubuntu 11.04 system, if I mark notify osd for installation in Synaptic, it says it will remove xfce4-notify and xubuntu-desktop.

---

### Post by moorhead98 on 2011-08-05
See, that's what I'm talking about. Isn't there any workaround to have Xubuntu desktop and Ubuntu desktop without removing each other and some of their components?
Sort of like when changing stuff in ccsm, and it gives you the option to disable one thing, the other thing, or [COLOR=Red]_**ignore**_[/COLOR] [COLOR=Black]the conflicts. 
[/COLOR]

---

### Post by moorhead98 on 2011-08-05
Or is there a way to just get the xfce desktop without removing Ubuntu? im ok without Xubuntu branded things. I'm just itching to try it out _***without ***_removing Ubuntu desktop (and Notify OSD)

---

### Post by rojaasensei on 2011-08-05
I originally installed ubuntu 11.04

Then I used this 

[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

which installed xubuntu, removing unity and gnome.  Works great.

Then I removed Abiword, Gnumeric and reinstalled Libre Office and all the apps I wanted, including most of the Ubuntu Studio packages.

Try the link if you like.  It details how to convert back and forth amongst Lubuntu, Xubunut, Gnome.

Keep in mind it is a long process, what with all the downloading.

---

### Post by moorhead98 on 2011-08-05
So that process deleted gnome as well? 
At this rate I wont be downloading Xubuntu any time soon

---

### Post by rojaasensei on 2011-08-05
Yes, as I recall it deleted everything except "Gnome User Guide."

But then, as many of us have discovered, with Xubuntu you end up not wanting a second desktop.  Xubuntu is so customizable, light, and fast.

Good luck!

---

### Post by moorhead98 on 2011-08-05
Well if i want something that is customizable, ill use kubuntu. If i want light and fast, ill use lubuntu. If i want something that  doesnt crash every other time i open something or doesn&#8217;t look like a baby blue version of windows xp, ill use Unity/gnome
But, I'll probably end up putting xubuntu on my cruddy desktop that has like no hardware acceleration that can barely do anything with natty. But I'm not giving up unity and compiz effects on my laptop
Plus, I don&#8217;t like downloading things that break other things. That's the number one reason i don&#8217;t have gnome 3. I love unity, and im not giving it up for something that looks confusing and downright strange

---

