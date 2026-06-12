---
title: "KDE on Ubuntu 7.10"
date: 2008-01-31
forum: Desktop Environments
---

### Post by SteveJM on 2008-01-31
I decided to add KDE desktop to my normal Ubuntu installation using :-

sudo apt-get install kubuntu-desktop

This installed fine, I can now choose which desktop environment I want when I log in and KDE seems to be all there.  There are other issues to resolve, isolating the two environments being one of them, but there are other threads which should guide me through this.

The first problem is that KDE runs REALLY slowly.  Even the menus appear one line at a time.

Entering your password when prompted (e.g. when trying to access graphic settings - or add new software) takes ages for the *** to apear, by which time you've tried again and completely confused matters.

Is there something I'm overlooking?

I'm using an ATI 9600 graphics card on a 2500barton cored PC  Which normally runs great with gnome, compiz and all effects etc.

I'd look further into the graphics settings if I could actually get there.  In Gnome, even without the ATI drivers installed, the default setting were fine just couldn't enable desktop effects.

Currently KDE is basically unusable in it's current state.

Any suggestions?

---

### Post by dgray_from_dc on 2008-01-31
Take Kubuntu-Desktop out.  I've heard of problems like this before.

For some reason, having both ubuntu and kubuntu desktop packages on the same install hoses up the machine.  I'm no expert on it, just a trend I've noticed here in the forum.

I have read that installing kde-core works out fine.

Another option is dual-booting Ubuntu & Kubuntu if you want the full Kubuntu experience.

Instructions on how to remove kubuntu-desktop and all unecessary depedancies can be found here [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by SteveJM on 2008-01-31
Thanks, that was the decision I am rapidly coming to.:(

What I was hoping for was to be able to use either Gnome or KDE, have the benefits of each desktop environment, even if I had to isolate them to keep the menus clear of clutter (KDE stuff all over the Gnome menu etc)

I would have liked to be ably to run a second X session, windowed if possible / maybe full screen, which I could open up the KDE session from within Gnome and flick between the two.

If this was a possibility, ideally an installation option, it would satisfy both preferences. Would Kubuntu etc need to be a separate entity?

---

### Post by SteveJM on 2008-01-31
As you say, duel booting is option, but is it really necessary?  Surely Ubuntu can run more than one desktop environment like most other distros can.

---

### Post by jesusfreak107 on 2008-01-31
[http://www.kubuntu.org/](http://www.kubuntu.org/)

get the full Kubuntu. if you have a decent computer, it should work fine, and have the most impressive graphics display of all of them. especially with Beryl/Compiz/Compinz Fusion installed.  Dualbooting is fun, easy, and convenient.

---

### Post by dgray_from_dc on 2008-01-31
> Surely Ubuntu can run more than one desktop environment like most other distros can.

You can still install kde-core with no problems. I think the problem you're having comes from installing kubuntu-desktop and all of the accompanying dependencies.

The problem with trying to isolate ubuntu-desktop (Gnome + apps) and kubuntu-desktop (KDE + apps) is that they are somewhat compatible.  As such, apps from one show up and work in the other.

I don't know that there is a way to separate ubuntu-desktop and kubuntu-desktop aside from dual-boot.

These are two "suites" (so to speak) of software, some of which is compatible, some of which isn't.

You could also consider dual boot with a common home partition.

The convenience of simply selecting from the desktop manager would be great, but I don't know that it's possible.

---

### Post by hyperair on 2008-01-31
Strange that you face problems with this.. I've had no problems before. And I'have GNOME, KDE and KDE4 installed.

---

