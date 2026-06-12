---
title: "gnome 2.12.2"
date: 2005-12-10
forum: General Help
---

### Post by geonetrinity on 2005-12-10
I'm a newbie guys!!!

    Is there a way for us to update Ubuntu Gnome 2.12.1 --> Gnome 2.12.2 (since it out already), the same thing with Kubuntu:

----------------------
 For those Ubuntu loyalists who need the latest, greatest software on their computers, KDE 3.5 is available for Ubuntu 5.10 (Breezy). The packages are available for both i386 and AMD64 systems. If you'd like to install KDE 3.5 on your Breezy system, just follow these simple steps:

Login as root and run the following commands from the console

      wget [http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg](http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg)
      apt-key add kubuntu-packages-jriddell-key.gpg

Add the following lines to /etc/apt/sources.list

      # Ubuntu 5.10 KDE 3.5 Repository
      deb [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main

Run the following commands

      apt-get update
      apt-get dist-upgrade

Make sure to use dist-upgrade rather than upgrade, because some necessary files will be held back. Once you've completed the above steps, close all open applications and restart the X server by pressing CTRL+ALT+BKSPACE. Log back into your KDE desktop and you'll find that you're running a new shiny version.
----------------------

Have a nice day!!! c",)

---

