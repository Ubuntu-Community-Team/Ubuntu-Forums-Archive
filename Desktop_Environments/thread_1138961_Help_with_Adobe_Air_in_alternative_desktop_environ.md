---
title: "Help with Adobe Air in alternative desktop environment"
date: 2009-04-26
forum: Desktop Environments
---

### Post by cknight on 2009-04-26
Has anyone successfully been able to get Adobe Air applictions to run in a desktop environment which is not KDE or Gnome?  I'm running Xmonad (a tiling window manager) and am getting the following error when trying to get the BBC Iplayer Desktop application to run:

```
Unknown desktop manager, only Gnome and KDE are supported
```

Post 7 of [http://www.linuxquestions.org/questions/linux-software-2/tweetdeck-in-xubuntu-runs-but-blank-and-unresponsive-708867/](http://www.linuxquestions.org/questions/linux-software-2/tweetdeck-in-xubuntu-runs-but-blank-and-unresponsive-708867/) suggests that its possible by enabling gnome-keyring or kwallet.  Gnome-keyring-daemon already appears to be running on my machine but obviously no luck.  Any ideas out there?

---

### Post by marcog on 2009-05-25
I'm also having issues running adobe air (tweetdeck specifically) on xmonad. I get the following error:

```
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
Unknown desktop manager, only Gnome and KDE are supported
```

The application runs, but their is no response from clicking the buttons. Gnome-keyring-daemon is running.

Anyone?

---

### Post by foxy123 on 2009-06-21
> **cknight said:**
> Has anyone successfully been able to get Adobe Air applictions to run in a desktop environment which is not KDE or Gnome?  I'm running Xmonad (a tiling window manager) and am getting the following error when trying to get the BBC Iplayer Desktop application to run:

```
Unknown desktop manager, only Gnome and KDE are supported
```

Post 7 of [http://www.linuxquestions.org/questions/linux-software-2/tweetdeck-in-xubuntu-runs-but-blank-and-unresponsive-708867/](http://www.linuxquestions.org/questions/linux-software-2/tweetdeck-in-xubuntu-runs-but-blank-and-unresponsive-708867/) suggests that its possible by enabling gnome-keyring or kwallet.  Gnome-keyring-daemon already appears to be running on my machine but obviously no luck.  Any ideas out there?

I have the same problem with Xubuntu 9.04 and BBC Desktop Player. Any luck with resolving Adobe AIR issue?

---

### Post by drader on 2009-10-24
Perhaps the forum link mentioned above was updated at a later point; however, I am able to follow @jua03 suggestion of the following:

$ GNOME_DESKTOP_SESSION_ID="whatever" /opt/TweetDeck/bin/TweetDeck

This appears to work for other *.air apps as I'm not trying to get tweetdeck running (I'm running Orsiso). Works fine for me as follows:

$ GNOME_DESKTOP_SESSION_ID="whatever" ~/apps/Orsiso/bin/Orsiso

Hope this helps,
drad

---

### Post by mistertim on 2010-05-04
I'm running xmonad instead of metacity as the window manager within gnome, and tweetdeck works fine. There's comprehensive instructions in the XMonad docs, and more details here: [http://www.lindenlan.net/2010/03/20/gnome-xmonad-on-karmic-koala/](http://www.lindenlan.net/2010/03/20/gnome-xmonad-on-karmic-koala/).

Tim

---

### Post by Jack Waugh on 2011-03-18
OK I found a way to get TweetDeck working on Xubuntu.  First off, one exports GNOME_DESKTOP_SESSION_ID=1 (I don't know why 1 or what it means), and secondly, one must run it on the local console of the computer, not via ssh -X.

---

