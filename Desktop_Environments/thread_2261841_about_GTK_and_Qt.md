---
title: "about GTK and Qt"
date: 2015-01-21
forum: Desktop Environments
---

### Post by nep-nori on 2015-01-21
I've been a Lubuntu die-hard fan ever since I first discovered Linux and it was the distro that allowed me to switch to Linux full-time, however recently I had to switch to "vanilla" Ubuntu built up from the netboot mini.iso due to compatibility issues and I installed XFCE as my DE to give it a go. I don't like XFCE very much, it looks better yes, but its behavior is nowhere near as smooth as that of LXDE.

Anyway... now that LXQt is meant to be "usable in a production environment", and because I'm very much an illiterate heathen when it comes to the subject matter of the inner workings of OS's and DE's, I thought I'd start this thread to ask the following question:

to an end user (and a particullary UNskilled one, such as myself) what does it imply to switch from a GTK-based DE to a Qt-based one?

specifically, I know GTK apps work on Qt environments and viceversa for the most part, but I also know that sometimes a single app for a specific DE requires quite a bit of GTK or Qt packages to run, and my comp is a glorified toaster that can't afford to install anything other than the bare-bones essential.

---

### Post by grahammechanical on 2015-01-21
Look at it this way. GTK and Qt are simply different tool kits for building software.

> **GTK+ (previously [B][GIMP]("http://en.wikipedia.org/wiki/GIMP") Toolkit, sometimes incorrectly referred to as the GNOME Toolkit) is a [cross-platform]("http://en.wikipedia.org/wiki/Cross-platform")[SUP][[3]]("http://en.wikipedia.org/wiki/GTK%2B#cite_note-3")[/SUP] [widget toolkit]("http://en.wikipedia.org/wiki/Widget_toolkit") for creating [graphical user interfaces]("http://en.wikipedia.org/wiki/Graphical_user_interface"). It is licensed under the terms of the [GNU LGPL]("http://en.wikipedia.org/wiki/GNU_Lesser_General_Public_License"), allowing both [free]("http://en.wikipedia.org/wiki/Free_software") and[proprietary]("http://en.wikipedia.org/wiki/Proprietary_software") software to use it. It is one of the most popular toolkits for the [Wayland]("http://en.wikipedia.org/wiki/Wayland_(display_server_protocol)") and [X11]("http://en.wikipedia.org/wiki/X_Window_System_core_protocol") [windowing systems]("http://en.wikipedia.org/wiki/Windowing_system"), along with [Qt]("http://en.wikipedia.org/wiki/Qt_(toolkit)").[SUP][[4]]("http://en.wikipedia.org/wiki/GTK%2B#cite_note-4")[/SUP]**[/B]

[http://en.wikipedia.org/wiki/GTK%2B](http://en.wikipedia.org/wiki/GTK%2B)

> **Qt ([/]("http://en.wikipedia.org/wiki/Help:IPA_for_English")[&#712;]("http://en.wikipedia.org/wiki/Help:IPA_for_English#Key")[k]("http://en.wikipedia.org/wiki/Help:IPA_for_English#Key")[ju&#720;]("http://en.wikipedia.org/wiki/Help:IPA_for_English#Key")[t]("http://en.wikipedia.org/wiki/Help:IPA_for_English#Key")[/]("http://en.wikipedia.org/wiki/Help:IPA_for_English") "cute", or unofficially as Q-T *cue-tee[SUP][[9]]("http://en.wikipedia.org/wiki/Qt_%28software%29#cite_note-9")[/SUP][SUP][[10]]("http://en.wikipedia.org/wiki/Qt_%28software%29#cite_note-10")[/SUP]) is a [cross-platform]("http://en.wikipedia.org/wiki/Cross-platform") [application framework]("http://en.wikipedia.org/wiki/Application_framework") that is widely used for developing [application software]("http://en.wikipedia.org/wiki/Application_software") that can be run on various software and hardware platforms with little or no change in the codebase, while having the power and speed of native applications. ***

[http://en.wikipedia.org/wiki/Qt_%28software%29](http://en.wikipedia.org/wiki/Qt_%28software%29)

Developers have their reasons for preferring one tool kit over another. And these differences of opinions can lead to disputes which are nothing to do with us users. An application will run if the libraries for the tool kit are present on the system. Having libraries for different tool kits does take up space on the hard disk but I do not think that of itself is an issue for us users to worry about.

To satisfy yourself why not dual boot into another install of Lubuntu and install LXQT? Then you can test it out on your machine.

[http://askubuntu.com/questions/464741/how-to-install-lxqt-de-in-ubuntu-14-04-lts](http://askubuntu.com/questions/464741/how-to-install-lxqt-de-in-ubuntu-14-04-lts)

Regards.

---

### Post by vasa1 on 2015-01-21
> **nep-nori said:**
> ...
to an end user (and a particullary UNskilled one, such as myself) what does it imply to switch from a GTK-based DE to a Qt-based one?

specifically, I know GTK apps work on Qt environments and viceversa for the most part, but I also know that sometimes a single app for a specific DE requires quite a bit of GTK or Qt packages to run, and my comp is a glorified toaster that can't afford to install anything other than the bare-bones essential.
I've been following the development of LXQt and my impression (from using Lubuntu with LXQt at the time LXQt was at version 0.7) is that LXQt is marginally more demanding than LXDE. The devs are aware of this and are working on making LXQt less demanding. In any case, there's no urgency to switch if you're on Lubuntu 14.04 which is an LTS and which will receive essential updates for its life of three years.

---

