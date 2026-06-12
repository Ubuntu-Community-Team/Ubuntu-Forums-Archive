---
title: "Installing KDE apps in Gnome"
date: 2008-04-25
forum: Desktop Environments
---

### Post by duncanbourne on 2008-04-25
I'm running standard Ubuntu with Gnome, but my wife has just found an application she 'must have' which is for KDE.

If I install this through the package manager, will it screw everything up, or can I use KDE applications in Gnome?

Duncan

---

### Post by KOTAPAKA on 2008-04-25
No man it's cool. The only thing with installing KDE apps in Gnome is that it must install some KDE libraries and then install the application itself so it might require some more space (for example 30MB more). Another thing is if you try to open Help in the application you might not be able to but this does not affect any other functions of the application. So go ahead and install it. 

And lets not forget that you can actually install KDE and have Gnome and KDE. It's up to you. Both ways work fine.

Forgot to say that Synaptic and apt-get are not as good as aptitude. Best use aptitude for this purpose (not that synaptic won't do the trick): aptitude install *package* You can find the package via synaptic and use aptitude to install it. I don't want to mess your mind with this but aptitude resolves dependencies better and when uninstalling a program removes libs that are no longer used which apt-get and synaptic fail to do. KEEP IN MIND THAT IF YOU HAVE USED SYNAPTIC OR APT-GET APTITUDE WILL PROPOSE REMOVAL OF MOST OF YOUR SOFTWARE. IN THIS CASE USE aptitude keep-all. You can read some more if you **frequently** install programs. If you don't stick with synaptic.

---

### Post by FrozenFOXX on 2008-04-25
No, that wouldn't cause a problem.  The downsides are pretty minimal, as Kotapaka mentioned it'll have to grab some KDE libraries but will do nothing out of the ordinary and the libraries are (relatively) small.

The "big" downside you'll notice is that when initially loading KDE libraries it will take a little time (usually only a few seconds on a modern system, if that) while those libraries get cached.  A good example of this is when I load Gnome-Do on KDE, the very first time I load it up it takes a second to come up (in this case it had to load GTK/Gnome libraries).  This is because when using only Gnome apps your system only has to spend time loading the GTK libraries.  When you toss applications that need libraries from other graphical implementations (like Qt in the case of KDE apps) it's got to load those, too.  However, once loaded it'll respond as normal, just like the GTK apps.  It also should only affect the first time loading it up (thereafter it will be cached like any Gnome app)

Also if you poke around you should be able to find a few things to help make KDE/Qt applications look native in Gnome.  As I'm a Kubuntu user myself I can't really list off any URLs offhand but I remember seeing quite a bit about it so it shouldn't be too tough.  This usually only takes a few minutes to look into and believe me will make your desktop continue to feel more, "uniform," one of the big things lacking from some other operating system desktops.

But yeah, feel free to load up applications you like, Gnome, KDE, or otherwise.

---

