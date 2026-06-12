---
title: "How can I install Kubntu in Ubuntu 9.04 BUT keep all Ubuntu packages as default??"
date: 2009-06-04
forum: Desktop Environments
---

### Post by -=Ghost=- on 2009-06-04
Hi All.

Is it possible to install the Kubuntu KDE environment inside Ubuntu, BUT keep all Ubuntu's Packages as Default applications when I start a program??

For example. After I installed Kubuntu in the past (In Ubuntu). 
When I launched Any programs Kubuntu is in control of what Programs launch when I start a package etc etc...

How can I still have Ubuntu as my main default O/S.
And have Ubuntu's own programs start/launch when I decide to run a program or Downloaded Package etc??

I hope I have explained my issue clearly enough.

I am still enjoying learning about Ubuntu/Kubuntu

Thank's for any replies in advance

---

### Post by RyanVanDiemen on 2009-06-05
Hi, that`s interesting. Unfortunately, I have no idea how to do this, but I`d really be interested in why you would want to do that...

---

### Post by coffeecat on 2009-06-06
> **-=Ghost=- said:**
> For example. After I installed Kubuntu in the past (In Ubuntu). 
When I launched Any programs Kubuntu is in control of what Programs launch when I start a package etc etc...

How can I still have Ubuntu as my main default O/S.
And have Ubuntu's own programs start/launch when I decide to run a program or Downloaded Package etc??

I hope I have explained my issue clearly enough.


Not really. I'm deeply puzzled as to what you mean.

Ubuntu uses the Ubuntu desktop; Kubuntu uses the KDE desktop. If you install KDE apps in Ubuntu/gnome, you also get to install some KDE libraries so that they can run, but they will run well in gnome. For instance, if you install the disc burning app k3b, it will bring in some KDE dependencies and will then run happily in Ubuntu/gnome. The k3b app window will use KDE widgets and font styles, so will look slightly out of place on the gnome desktop, but apart from that it will run OK.

Similarly if you are running Kubuntu/KDE and install a gnome app, it will bring in some gnome libraries, but again will run OK in the KDE environment. **You** decide which application you launch.

If you are talking about installing the whole other desktop, this is slightly more involved, but you are still in charge. If you are running Ubuntu/gnome and want the KDE desktop the best way is to install the 'kubuntu-desktop' package which will install everything for what you need to run Kubuntu - default applications included. You will be asked to choose between the GDM (gnome) login manager and the KDM (KDE) login manager, and then when you get to login you can choose which desktop environment you want to log in to. You can also set which is the default desktop, gnome or KDE, so that if you do not make a choice at login, this is the desktop that loads.

Similarly, if you are running Kubuntu, you can install the Ubuntu version of gnome plus its default apps by installing 'ubuntu-desktop'.

The only (minor) complication is that the usplash bootup splash changes to the latest desktop installed. If you install kubuntu-desktop in Ubuntu, you get the blue Kubuntu usplash instead of the orange-red Ubuntu one. This is easily changed back by going from step 3 in this howto:

[https://help.ubuntu.com/community/USplash](https://help.ubuntu.com/community/USplash)

Does this answer your question?

**Edit:** but if you are referring to the default app that opens when you double-click on a filetype, both desktop environments have ways of setting the default.

---

### Post by Jack Crossen on 2009-06-06
You can, as suggested, download the Kubuntu-desktop metapackage in your Ubuntu 9.04 installation. 

I did what you are asking about - installed the Kubuntu-desktop in my Ubuntu 9.04 because I wanted to check out the KDE desktop. Doing that caused a variety of problems in my Ubuntu Gnome desktop e.g. icons in my Gnome Do dock that are for KDE only and are unusable in the Gnome (Ubuntu) environment, Kubuntu shutdown screen even though I logged into an Ubuntu session etc. 

After my experience and a little reflection it seems to me that if installing and using the KDE desktop environment in the Ubuntu default Gnome desktop environment worked well - there wouldn't be any reason for a separate Kubuntu distribution.

The Kubuntu-desktop file is called a metapackage because it includes maybe a hundred or so packages that are installed, that will not be removed if you run synaptic package manager and just remove Kubuntu-desktop...that makes it a bit of a challenge to remove, although not that difficult if you follow the instructions "Getting Back to a Pure Gnome On Ubuntu" at [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

After I deleted the Kubuntu-desktop meta packages I created a new partition on my hard drive and installed Kubuntu there. That works much better for me and allows me to check out what's going on with the KDE environment. If you have some spare room on your hard drive you might want to go that route.

---

