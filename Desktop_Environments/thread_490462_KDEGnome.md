---
title: "KDE/Gnome"
date: 2007-07-02
forum: Desktop Environments
---

### Post by kubilaycan on 2007-07-02
Hi. I am considering installing ubuntu. I have never used linux before but I think its about time to take a step forward..

The most important part of my pc is my music collection. I have been using winamp on windows so far for about 10 years. I came to realize that Amarok seems to be a better player than Rythmbox. Also amarok comes with kubuntu and rythmbox with ubuntu. 

I just have a couple of questions.

Since the only difference between ubuntu and kubuntu is gnome and kde, does that mean theoretically that if I install ubuntu and then get the KDE and remove  Gnome and all the gnome standard applications(if thats possible of course)  I will have exactly the same as installing kubuntu alone? 

Is there ANY drawback of having both desktop environments installed at the same time? If I install a program in the gnome environment will I be able to run it after switching to the KDE? Or do I have to install the same program seperately for each desktop environment? Are there any compatibility issues?

I also read that in order to use amarok, ubuntu only requires the KDE library or something like that. So basically I would not have to install the whole KDE package to run amarok on ubuntu. Will installing these libraries affect the performance of my computer in any way? I mean will it better to run amarok on kubuntu than ubuntu + kde libraries?

Please keep in mind that I really would like to use amarok, unless anyone can convince me there is a better player for linux. 

Also I would like to experiment with both desktop environments and then settle with one maybe. Unless it is guaranteed that having both will have no effect on system performance.

Regards...

Sorry for being a newbie.

---

### Post by smartboyathome on 2007-07-02
For an Amarok-type player on GNOME, there is Exaile. Its main goal is to create an amarok-type player for GTK+. Since this runs natively in GNOME, I would use it on ubuntu instead of amarok.

Anyway, I would advise against installing both KDE and GNOME on an ubuntu installation, simply because the menus and such become cluttered and they both don't use the same interface, so even though you have items on one, the other might not be able to use it. If you REALLY want to test both, I would suggest getting ubuntu and kubuntu separate and installing them. Also, they take up a lot of space, leaving you less space for your files.

Now to your first question. It is possible to get rid of gnome and only have KDE, but you would have to find a guide for it. There is no easy tway to "remove" Gnome unless you want to go through all the packages in Synaptic and remove the ones that belong to Gnome.

I hope this helps you!
Smartboy :)

---

### Post by peter_k on 2007-07-02
I run ubuntu feisty, and have both gnome and KDE installed, and haven't had any issues.  I'm primarily a gnome user, because I like the uncluttered interface, I find it aesthetically pleasing, and for some reason the menu structure in Gnome seems better to me (although I could see why people would like KDE as well); I do boot into KDE once in a while, mostly to "mess with" (customize) the desktop, and the only difference I see is that I sometimes have issues trying to find things, because they're not always in the same place (i.e. add programs and synaptic in particular), but I am always able to find it.

I know that some programs (Amarok comes to mind) are really "designed" for KDE, but I do run it in Gnome and haven't run into any major stumbling blocks (I also have Exaile, but as it can't seem to read my m3u files as easily as Amarok does, I use Amarok.  If I could get Exaile to work well with my m3u files, I may very well use it).  As for the space issue, I'm lucky enough to have plenty of HDD room, but I could see where that would be an issue for some.

To me, it's really just a matter of personal choice, and what better choice than to have access to both - that way, if you are having a "KDE day" just boot into it, and the same for Gnome (or an XFCE day, enlightenment day, etc..)  Keep in mind that this is a luxury Windows users don't have, so the choice aspect is one thing (among many) that makes Linux great.

---

### Post by Nythain on 2007-07-02
You can run kde apps in gnome and gnome apps in kde... and on a decent machine you can do it with little to no noticeable performance loss...

so what i would recommend is figure out wich Desktop Environment you like better (i was geared more towards kde), then install the flavor of ubuntu for it (ubuntu for gnome, kubuntu for kde) then just install whatever apps you want from the other DE... like i would install synaptic and firefox on my kubuntu system, just because konqueror not that great of a web browser and adept BLOWS

Others go the other route, and install ubuntu for the generall gnome set up, then install what they want kde wise, like amarok, kopete, k3b, and a few other apps people consider necessary, or superior to the gtk alternatives

---

### Post by bg1256 on 2007-07-02
You can run amarok just fine in Gnome with no problems at all.

I personally use KDE, but I'm thinking about switching back to Gnome... still thinking about it though.

I've used amarok in Gnome and KDE, and it works fine in both.

---

### Post by darrenm on 2007-07-02
I use Amarok in gnome, no problems. Can't get on with Exaile. I will be changing to KDE 4 in October though :)

---

### Post by peter_k on 2007-07-03
> **darrenm said:**
>  I will be changing to KDE 4 in October though :)

That's in a nutshell why I have them both installed...I'm satisfied with Gnome, but if it turns out that KDE 4 is so much better, I'm upgrading rather than doing a full KDE install, and I'll already be at least a little familiar with the interface.  The same logic would apply (to me, at least) if I was using KDE and it turned out Gnome 2.20 was better.

---

### Post by Survivalism on 2007-07-07
Is there a way to keep the KDE apps from appearing in the menu on Gnome, and vice versa?  I would like to toy around with KDE, but I hate that it combines both menus, and I have about 17 million apps in both environments.

---

### Post by Happy_Man on 2007-07-07
> **Survivalism said:**
> Is there a way to keep the KDE apps from appearing in the menu on Gnome, and vice versa?  I would like to toy around with KDE, but I hate that it combines both menus, and I have about 17 million apps in both environments.
I think the only way is to manually edit the K menu from the Menu Editor (accessed by right-clicking the K Button and choosing Edit Menu).

---

### Post by strabes on 2007-07-21
Two options:

1) sudo aptitude remove kubuntu-desktop and just install kde-core. Then it wouldn't install all the apps that come with kubuntu, just the libs necessary to run kde. You could install just the apps you wanted to.

2) Just remove the menu items using alacarte in gnome and the built-in kde menu editor via the right click menu.

---

### Post by EtniesBMX on 2007-10-16
> **Happy_Man said:**
> I think the only way is to manually edit the K menu from the Menu Editor (accessed by right-clicking the K Button and choosing Edit Menu).

Here is a very convenient solution for KDE users who want a menu with consolidated Gnome applications: [http://kde-apps.org/content/show.php/K+Menu+Gnome+(Debian+Package)?content=31031]("http://kde-apps.org/content/show.php/K+Menu+Gnome+(Debian+Package)?content=31031")

I use it, and it works great.


> Now to your first question. It is possible to get rid of gnome and only have KDE, but you would have to find a guide for it. There is no easy tway to "remove" Gnome unless you want to go through all the packages in Synaptic and remove the ones that belong to Gnome.

As far as removing Gnome and all Gnome apps after installing KDE, it actually IS possible without unchecking/checking individually in Synaptic or Adept: [http://psychocats.net/ubuntu/purekde]("http://psychocats.net/ubuntu/purekde")


> Anyway, I would advise against installing both KDE and GNOME on an ubuntu installation, simply because the menus and such become cluttered and they both don't use the same interface, so even though you have items on one, the other might not be able to use it. If you REALLY want to test both, I would suggest getting ubuntu and kubuntu separate and installing them. Also, they take up a lot of space, leaving you less space for your files.

Reinstalling or doing a dual boot just to figure out which you prefer would be a HUGE waste of time. The only convenience you're gaining with two separate installations is not having cluttered menus, which is not a deciding factor for me and most likely not for you. If it is, by all means do a dual installation. However, a more practical way is to install them side-by-side with a package manager (see above psychocats link). Once you decide, you can remove the desktop environment you don't prefer using the psychocats tutorial above

Amarok works great for me and works very well with my iPod.

Good luck

---

### Post by TeaSwigger on 2007-10-17
Hello kubilaycan,

I'm also a music lover. Besides Amarok, Exhaile and Rhythmbox, you might be interested in gmusicbrowser, particularly if your collection is very large:

[http://squentin.free.fr/gmusicbrowser/gmusicbrowser.html](http://squentin.free.fr/gmusicbrowser/gmusicbrowser.html)

Works fine in ubuntu or kubuntu. :)

---

### Post by mexlinux on 2007-10-17
KDE and GNOME apps are just linux apps written with a different toolkit.
They can live together in the same desktop.

---

