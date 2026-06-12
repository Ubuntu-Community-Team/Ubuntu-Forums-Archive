---
title: "Can I use the same user profile between GNOME and KDE?"
date: 2010-07-07
forum: Desktop Environments
---

### Post by DJ_Peng on 2010-07-07
I've been using Ubuntu with GNOME for the past few years and I'm looking at possibly switching to the KDE-based Kubuntu. I know I can have both DE's on my system and even found a [tutorial on the Psychocats site]("http://www.psychocats.net/ubuntu/kde") for setting it up, but I have a question for the KDE gurus here. Can I safely use the same user profile between both GNOME and KDE or should I set up a new user for working in KDE? I haven't seen anything saying I can't but I really don't want to hose my GNOME settings in case I end up not liking KDE enough to use it on a daily basis.

---

### Post by Yarui on 2010-07-07
Gnome and KDE settings are maintained separately.  At the login screen you can choose your desktop environment if you have more than one installed.  The only downside of using both Gnome and KDE is that your menus will be a bit cluttered as they will have both Gnome and KDE applications in them.

---

### Post by DJ_Peng on 2010-07-07
That's fantastic news. I didn't realize the settings were stored separately. That will make it much easier to give KDE a whirl.

I don't mind having long menus. I already have some KDE apps installed, and I can always disable menu entries if I need to.

---

### Post by Yarui on 2010-07-07
That's true, it is fairly easy to customize the menus to display only what you want them to.  It is definitely no problem to try out KDE.  I did a few weeks ago and it was kind of buggy on my machine so I decided to uninstall it.

It wasn't very difficult to completely remove it.  The only setting that seemed to linger after going back into gnome was that the mouse pointer looked like the KDE mouse pointer and I couldn't seem to get it back to the Gnome pointer.  I finally fixed it by finding the package with the KDE mouse pointer and uninstalling it.  After that everything was back to the way it was before I installed KDE.

---

### Post by DJ_Peng on 2010-07-07
Good to hear. I've been getting more and more dissatisfied with Ubuntu in recent releases and I'm hearing KDE has improved a lot since I last tried it two years ago. I'm going to run the tutorial now and give it a spin.

It's too bad Kubuntu uses Plymouth for the boot splash since it's quite borked on my system.

---

### Post by DJ_Peng on 2010-07-07
Crap! I logged into a KDE session and my desktop is a blank white! I don't even see the KDE bottom panel or any wallpaper. Anyone know what I may have missed on my installs?

---

### Post by Yarui on 2010-07-07
Did you install KDE through the synaptic package manager or through Ubuntu Software Center?  If you search Ubuntu Software Center for Kubuntu you will find an installer called "Kubuntu Plasma Desktop System".  This is a meta package that installs everything you need for KDE on an Ubuntu Desktop.  If you are using a netbook you can instead choose the "Kubuntu Plasma Netbook System" meta package.  Don't worry about getting rid of the stuff you have already installed, it won't interfere with the installation of this package and everything you installed already is most likely required anyway.

---

### Post by KdotJ on 2010-07-07
You can also install KDE-minimal package in Synaptic. It will install KDE but miss out on some of the apps and other bloat

---

### Post by Yarui on 2010-07-07
> **KdotJ said:**
> You can also install KDE-minimal package in Synaptic. It will install KDE but miss out on some of the apps and other bloat
This probably wouldn't be a bad idea, considering I felt KDE was a bit slow on my machine.  It could be because I followed this method of installation that put practically everything available onto my machine.

---

### Post by DJ_Peng on 2010-07-09
> **Yarui said:**
> Did you install KDE through the synaptic package manager or through Ubuntu Software Center?  If you search Ubuntu Software Center for Kubuntu you will find an installer called "Kubuntu Plasma Desktop System".  This is a meta package that installs everything you need for KDE on an Ubuntu Desktop.  If you are using a netbook you can instead choose the "Kubuntu Plasma Netbook System" meta package.  Don't worry about getting rid of the stuff you have already installed, it won't interfere with the installation of this package and everything you installed already is most likely required anyway.
I started in USC to get the main Plasma desktop and then moves to Synaptic to get other things I knew/thought I'd want. One of today's tasks is to see what app installing methods are available with KDE.

> **KdotJ said:**
> You can also install KDE-minimal package in Synaptic. It will install KDE but miss out on some of the apps and other bloat
I wish I knew this the other day. ;) Oh well.

> **Yarui said:**
> This probably wouldn't be a bad idea, considering I felt KDE was a bit slow on my machine.  It could be because I followed this method of installation that put practically everything available onto my machine.
KDE is being kind of slow, but I suspect it's because I do still have some GNOME and general GTK apps running, like Do. As I tweak things I'm killing GNOME things that I don't need as I run KDE, but I definitely need to find a good package manager with the flexibility of Synaptic for finding and reinstalling things.

I also want to check out some of the alternative apps people have told me about. One thing I've found already is that Konqueror seems to be worse than Epiphany/WebKit. I can't even check Gmail properly in Konqueror, which is really disappointing. Luckily Chromium seems to be playing nicely with KDE.

The one big problem I'm seeing so far is that Plasma crashes every now and then and dumps me to my old desktop. Is there a way to restart Plasma without logging out?

Two other things I'm needing to find are how to pull things on top (Do always opens in the background) and if there's a way to enable window shading with the mouse? I love having that from Compiz but KWin doesn't seem to be that flexible.

---

