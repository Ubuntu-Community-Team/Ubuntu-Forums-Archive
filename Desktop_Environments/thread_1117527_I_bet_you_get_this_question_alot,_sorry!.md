---
title: "I bet you get this question alot, sorry!"
date: 2009-04-06
forum: Desktop Environments
---

### Post by Eikuy on 2009-04-06
Hope this is the correct place.

Soo...something everyone is propably dead-bored answering to, i did search for this already, but i would like just one more final mash-up. Just to make it clear enough for me.

Gnome, KDE or XFCE? (I can hear  you sigh)

So there is no real difference in how these desktops work? The ONLY difference is GUI? So anything i can install on Ubuntu i can also install on Kbuntu and Xbuntu?

And about Xbuntu. What kind of downsides is there on Xbuntu? (I mean, its lighter to run than ubuntu, there got to be some minuses - if not, why would anyone choose ubuntu over Xbuntu besides the looks?)

I got this lousy 1,5Ghz processor with 500-whatever memory. I believe Xbuntu would be a smart choice for such machine, but im afraid there is some major downsides on Xbuntu or something.

And one more little thing, if i install Ubuntu and then, for example, Kubuntu desktop, does it take much more HD space? And can i share the apps and programs between those two? 

Thanks.

EDIT:

I just found out KDE and Gnome uses different apps. Sry for bothering. So how about Gnome and XFCE? And how many different apps would i need to get?

---

### Post by mcduck on 2009-04-06
You can install any of them on any Ubuntu version, and ou can have as many desktop environments and window managers as you ever want installed at the same time. If you have more than one installed you can select which one to use at the login screen.

Adding extra desktop environments will only take some disk space but won't slow your machine down (as only one of them is running at a time).

You can run the same programs in any desktop environment, but since Gnome and KDE use different toolkits the programs from another DE will look different than native programs do. And using programs made for another DE often require loading some libraries for that DE as well, which slightly increases memory usage. Usually this is meaningless but on a machine with low RAM it's at least worth knowing this.

When compared to Gnome, XFCE is a bit more lightweight, with a bit less features. Mostly the kind of things that are not immediately visible to the user like drag&dropping stuff between programs, built-in support for FTP and different network shares etc. In other words, lots of small things that might or might not be important to you.

In the end, nobody else will be able to tell you which one you like best. You'll just have to try them yourself. Since you have fairly low amount of RAM I'd recommend giving XFCE a try.

---

### Post by rwmuller on 2009-05-30
Following up there is a brief tutorial with an excellent listing of alternate desktop environments and the installation script from [Ubuntu Tutorials]("http://ubuntu-tutorials.com/2006/12/18/alternate-desktop-managers-kde-xfce-enlightenment-fluxbox-ubuntu-6061-610/")

Good piece on [installing KDE]("http://www.psychocats.net/ubuntu/kde"),  This is very complete and explains some of the drawbacks. 

Be aware that when you install a desktop environment you will also install its tools.  This can create some crowding in your menus.  KDE particualarly has its own tool set.  It is not a easy to uninstall as it is to install.  Still there is little cost (except drive space) to installing new environments.  

I am currently running xfcm, KDM and gnome on by laptop, with all those and fluxbox on my desktop.  All on  Intrepid.

My biggest problem is accessing network drives.  I have a 1Tb net storage device hung off my wireless router.  Gnome make it easy to access shares on this drive.  I have now learned to use look for the network tab in KDE.  I have mounted the drives in xfce but I can't find them in application menus or the file system.

If, like me, you installed Ubuntu to learn about Linux and try it out you owe it to yourself to install at least KDE and xfce.  These two alternates are very different from gnome and offer a very different experience.  You may find you like them or like me, you may find you use each of them at different times.
Enjoy

---

### Post by WatchingThePain on 2009-05-30
I tried XFCE in order to streamline.
It is a nice good DE but coming from the Ubuntu Gnome desktops rich experience I went back to Gnome.
If my pc was really low on resources I would use XFCE or something similar.

---

### Post by Alexis Phoenix on 2009-05-30
I agree with all the above - but - it may be worth knowing that when you start a KDE application when you're using Gnome, it will also run a small server program in the background to support your app.  This will increase the startup time for the first KDE app (and you may get some error message), but after that all will be good.  If you run a Gnome application from within KDE, you will find things start more quickly if there is already a Gnome app running, for similar reasons.

Personally I prefer Gnome - KDE reminds me of Windows too much!

On the subject of low resources - I have a laptop I used until a couple of years ago with only a 500MHz CPU, and low RAM (can't remember amount - maybe 64MB or 128MB) which runs fine with Debian (on which Ubuntu is based of course), a 2.4 series kernel and the WindowMaker desktop.  If you are stuck with low resources, or just want a faster experience, I recommend WindowMaker!

Have a lot of fun!  (oh wait, that's another distro innit...) I'll go away now....

---

### Post by WatchingThePain on 2009-05-30
> **Alexis Phoenix said:**
> I agree with all the above - but - it may be worth knowing that when you start a KDE application when you're using Gnome, it will also run a small server program in the background to support your app.  This will increase the startup time for the first KDE app (and you may get some error message), but after that all will be good.  If you run a Gnome application from within KDE, you will find things start more quickly if there is already a Gnome app running, for similar reasons.

Personally I prefer Gnome - KDE reminds me of Windows too much!

On the subject of low resources - I have a laptop I used until a couple of years ago with only a 500MHz CPU, and low RAM (can't remember amount - maybe 64MB or 128MB) which runs fine with Debian (on which Ubuntu is based of course), a 2.4 series kernel and the WindowMaker desktop.  If you are stuck with low resources, or just want a faster experience, I recommend WindowMaker!

Have a lot of fun!  (oh wait, that's another distro innit...) I'll go away now....

Thanks for that info about app startup times.
I never knew about that.
So I guess that means more overhead if using say kde apps on Gnome or vice versa.
Gnome is what I use.
I don't know if that's because I started out with Gnome.
XFCE was impressive, I like the little mouse icon.
Apparently KDE and Gnome are about equal in the resources they use.
LXDE was another good one I recall.

---

### Post by Alexis Phoenix on 2009-05-31
Glad to be of help - I forgot, the other lightweight WM I think really rocks is Enlightenment - I don't know if there has been much recent development on it though.

---

