---
title: "Uninstalling Xubuntu and returning to Ubuntu"
date: 2014-10-05
forum: Desktop Environments
---

### Post by Brandon_MacEachern on 2014-10-05
14.04

I'm having a problem removing Xubuntu, so I can return to regular Ubuntu.  I tried removing:

```
sudo apt-get remove abiword abiword-common abiword-plugin-grammar abiword-plugin-mathview alacarte bison blueman brltty-x11 catfish espeak exo-utils flex fonts-droid fonts-lyx gigolo gmusicbrowser gnome-system-tools gnome-time-admin gstreamer0.10-gnomevfs gthumb gthumb-data gtk2-engines-pixbuf indicator-application-gtk2 indicator-sound-gtk2 leafpad libbison-dev libdigest-crc-perl libexo-1-0 libexo-common libexo-helpers libfl-dev libgarcon-1-0 libgarcon-common libgdome2-0 libgdome2-cpp-smart0c2a libglade2-0 libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra libgsf-1-114 libgsf-1-common libgstreamer-perl libgtk2-notify-perl libgtk2-trayicon-perl libgtkmathview0c2a libgtkspell0 libido-0.1-0 libindicate-gtk3 libintl-perl libjpeg-progs libjpeg-turbo-progs libkeybinder0 liblink-grammar4 libloudmouth1-0 libnet-dbus-perl liboobs-1-5 libots0 librarian0 libsexy2 libtagc0 libthunarx-2-0 libtidy-0.99-0 libtie-ixhash-perl libtumbler-1-0 libunique-1.0-0 libvte-common libvte9 libwv-1.2-4 libxfce4ui-1-0 libxfce4ui-utils libxfce4util-bin libxfce4util-common libxfce4util6 libxfcegui4-4 libxfconf-0-2 libxml-parser-perl libxml-twig-perl libxml-xpath-perl lightdm-gtk-greeter link-grammar-dictionaries-en m4 orage parole pastebinit pavucontrol pidgin pidgin-data pidgin-libnotify pidgin-microblog pidgin-otr plymouth-theme-xubuntu-logo plymouth-theme-xubuntu-text python-configobj rarian-compat ristretto screensaver-default-images scrollkeeper shimmer-themes system-tools-backends tcl8.5 thunar thunar-archive-plugin thunar-data thunar-media-tags-plugin thunar-volman tumbler tumbler-common xbrlapi xchat xchat-common xfburn xfce-keyboard-shortcuts xfce4-appfinder xfce4-cpugraph-plugin xfce4-dict xfce4-indicator-plugin xfce4-mailwatch-plugin xfce4-netload-plugin xfce4-notes xfce4-notes-plugin xfce4-notifyd xfce4-panel xfce4-places-plugin xfce4-power-manager xfce4-power-manager-data xfce4-quicklauncher-plugin xfce4-screenshooter xfce4-session xfce4-settings xfce4-systemload-plugin xfce4-taskmanager xfce4-terminal xfce4-verve-plugin xfce4-volumed xfce4-weather-plugin xfce4-xkb-plugin xfconf xfdesktop4 xfdesktop4-data xfwm4 xscreensaver xscreensaver-data xscreensaver-gl xubuntu-artwork xubuntu-default-settings xubuntu-desktop xubuntu-docs xubuntu-icon-theme xubuntu-wallpapers 
```

Then installing:

```
sudo apt-get install ubuntu-desktop
```

And while it boots up correctly, shows the regular Ubuntu splash and login screen, you can NOT log in, it just says failed to start session.  Even the guest can't login.  What did I do wrong?

---

### Post by vasa1 on 2014-10-06
Where did you get that list from? Do you know if that list is applicable to current versions of *buntu? The psychocats list is no longer maintained and may not apply to 14.04.

ubuntuforums.org/showthread.php?t=416802&p=12695426

---

### Post by Brandon_MacEachern on 2014-10-06
I got it from:  [http://askubuntu.com/questions/436806/how-to-completely-remove-xubuntu-and-install-ubuntu-including-boot-screen-etc](http://askubuntu.com/questions/436806/how-to-completely-remove-xubuntu-and-install-ubuntu-including-boot-screen-etc)

Which in the answers section was updated for 14.04.

Either way, I would assume reinstalling the ubuntu desktop metapackage should install everything properly.

---

### Post by vasa1 on 2014-10-06
One difference could be that that person already had a functional Ubuntu and wanted to remove unwanted xubuntu components.

---

### Post by Brandon_MacEachern on 2014-10-06
I don't know, but it was the only thing I can find.

I really need this fixed though, it's my desktop and I need an easy way to restore this without loosing anything.

---

### Post by BBQdave on 2014-10-07
> **Brandon_MacEachern said:**
> ...it's my desktop and I need an easy way to restore this without loosing anything.

There can be problems removing Xubuntu, as it may pull shared dependencies (system programs that Ubuntu needs too) - easiest way, copy your data to separate drive and fresh install of Ubuntu Unity :)

---

### Post by grahammechanical on 2014-10-07
This may help

[http://itsfoss.com/failed-to-start-session-ubuntu-14-04/](http://itsfoss.com/failed-to-start-session-ubuntu-14-04/)

But note, the alternative method listed further down the page is to install an alternative desktop. But it will get you to a working desktop. I have gnome-session-flashback installed in 14.04 to use as an alternative. I get two additional login options - Gnome Flashback (Compiz) and Gnome Flashback (Metacity). The first is useful if I mess up Unity. The second is useful if I mess up Compiz. I expect gnome-session-flashback to be a smaller package than the full Gnome 3 shell with its ubuntu-gnome desktop that is offered in that link.

Regards.

---

### Post by Brandon_MacEachern on 2014-10-07
> **BBQdave said:**
> There can be problems removing Xubuntu, as it may pull shared dependencies (system programs that Ubuntu needs too) - easiest way, copy your data to separate drive and fresh install of Ubuntu Unity :)
Being how easy it is to go to say Xubuntu or Kubuntu, it seems like a bad metapackage if you can't return to Ubuntu with their metapackage.

Seems like with everything Ubuntu, make one wrong move, and it's an entire system reinstall all over again.  Gets old.

---

### Post by Brandon_MacEachern on 2014-10-07
> **grahammechanical said:**
> This may help

[http://itsfoss.com/failed-to-start-session-ubuntu-14-04/](http://itsfoss.com/failed-to-start-session-ubuntu-14-04/)

But note, the alternative method listed further down the page is to install an alternative desktop. But it will get you to a working desktop. I have gnome-session-flashback installed in 14.04 to use as an alternative. I get two additional login options - Gnome Flashback (Compiz) and Gnome Flashback (Metacity). The first is useful if I mess up Unity. The second is useful if I mess up Compiz. I expect gnome-session-flashback to be a smaller package than the full Gnome 3 shell with its ubuntu-gnome desktop that is offered in that link.

Regards.
I might try installing Gnome flashback.  Didn't try that one.  Tried re configuring packages, and that didn't work.

---

### Post by scoon on 2014-10-07
Hey there, 

I did a similar thing.  I removed kubuntu for Ubuntu.  Interestingly, I also had the same log in problem.  First check /var/log/lightdm/lightdm.log for a clue.  My problem was that kubuntu installs a custom config file for lightdm.  This old config was preventing the session to start.  To resolve this, I moved, not copy, /etc/lightdm into /root (for safe keeping).  Then I made sure the lightdm service was stopped and re-installed it.  Once that was done, I started the lightdm service and the session started just fine.

good luck, 

Skip

---

### Post by Brandon_MacEachern on 2014-10-08
> **scoon said:**
> Hey there, 

I did a similar thing.  I removed kubuntu for Ubuntu.  Interestingly, I also had the same log in problem.  First check /var/log/lightdm/lightdm.log for a clue.  My problem was that kubuntu installs a custom config file for lightdm.  This old config was preventing the session to start.  To resolve this, I moved, not copy, /etc/lightdm into /root (for safe keeping).  Then I made sure the lightdm service was stopped and re-installed it.  Once that was done, I started the lightdm service and the session started just fine.

good luck, 

Skip
You know what, I think you're right, because it does set Xubuntu as the default, and bam, if it's not there, it's not going to know what to do nor show us an option if Unity is the only thing present, while the configuration is pointing to a nonexistant window manager.  I think you just solved it.  I'll be trying this tonight when I get home from work.  If this works, I owe you a beer.

---

### Post by BBQdave on 2014-10-08
> **Brandon_MacEachern said:**
> Seems like with everything Ubuntu, make one wrong move, and it's an entire system reinstall all over again.  Gets old.

If your exploring different **D**esktop **E**nvironments, you can just leave it on your system, and choose the one you like... go for awhile, then try another. Not sure why folks like to check out DE's then remove them.

On a side note, loaded Ubuntu Unity 14.04 at release - I like Unity, and remarkably stable, for just released. I've been cruising along with out issue since install. Personally, I find little lacking with the default Ubuntu Unity + Google Chrome :)

---

### Post by scoon on 2014-10-08
> **Brandon_MacEachern said:**
> You know what, I think you're right, because it does set Xubuntu as the default, and bam, if it's not there, it's not going to know what to do nor show us an option if Unity is the only thing present, while the configuration is pointing to a nonexistant window manager.  I think you just solved it.  I'll be trying this tonight when I get home from work.  If this works, I owe you a beer.

I sure hope so.  I love me some beers.......

---

### Post by Brandon_MacEachern on 2014-10-08
> **BBQdave said:**
> If your exploring different **D**esktop **E**nvironments, you can just leave it on your system, and choose the one you like... go for awhile, then try another. Not sure why folks like to check out DE's then remove them.

On a side note, loaded Ubuntu Unity 14.04 at release - I like Unity, and remarkably stable, for just released. I've been cruising along with out issue since install. Personally, I find little lacking with the default Ubuntu Unity + Google Chrome :)
I don't like the clutter from having more than one desktop.  Each desktop installed has it's own tools, etc and it just all adds to a clutter.  So I remove the old desktop so I can a clean experience each time.

---

### Post by Brandon_MacEachern on 2014-10-09
> **scoon said:**
> I sure hope so.  I love me some beers.......
Got home, tried it, worked.  :D  So happy.

Only quirk though, Terminal, and Nautilus has a regular menu bar, it's not integrated into the title bar or the menu bar like it should be.  So far other applications seem to be ok.  Not a huge thing but I wonder what caused this weird unintegration.  There may be more applications but not all of them are affected.

---

### Post by Brandon_MacEachern on 2014-10-09
This is definitely still not a complete metapackage.  I still feel the metapackage for Ubuntu desktop is incomplete.

System Monitor is missing the tab about system information, menu bar integration is basically broken, and scrollbar overlay is missing.  It's not a good Unity experience I should be seeing.  So something is still very wrong here.

EDIT:
Fixed the menu bar by installing unity-gtk3-module, and unity-gtk2-module.  Fixed the scrollbar thing by installing that module too.

Only thing not fixed is the system monitors tab that shows system information but that is so minimal, i can just use the regular details tab in system settings.  But hey, any advice is highly appreciated.

So I do owe you a beer.  ;)  You figured it out, and saved me a complete reinstall, thanks!

---

### Post by scoon on 2014-10-09
> **Brandon_MacEachern said:**
> This is definitely still not a complete metapackage.  I still feel the metapackage for Ubuntu desktop is incomplete.

System Monitor is missing the tab about system information, menu bar integration is basically broken, and scrollbar overlay is missing.  It's not a good Unity experience I should be seeing.  So something is still very wrong here.

EDIT:
Fixed the menu bar by installing unity-gtk3-module, and unity-gtk2-module.  Fixed the scrollbar thing by installing that module too.

Only thing not fixed is the system monitors tab that shows system information but that is so minimal, i can just use the regular details tab in system settings.  But hey, any advice is highly appreciated.

So I do owe you a beer.  ;)  You figured it out, and saved me a complete reinstall, thanks!

Hey there, 

Have you tried apt-get check or apt-get install --reinstall ubuntu-desktop?  They may get you sorted out.

Thanks, 

Skip

---

### Post by Brandon_MacEachern on 2014-10-09
Yea it didn't work for the missing system tab.  It's not a huge deal so I won't care too much about it.

---

### Post by mechanic on 2014-10-10
> **Brandon_MacEachern said:**
> 14.04

I'm having a problem removing Xubuntu, so I can return to regular Ubuntu. ...



Glad to see you fixed most problems in the end. But why change from xubuntu to the parent ubuntu/unity?

---

### Post by scoon on 2014-10-10
> **mechanic said:**
> Glad to see you fixed most problems in the end. But why change from xubuntu to the parent ubuntu/unity?

I'd be willing to bet you could ask 100 different people and probably get about 100 different reasons.  I switched from Kubuntu to Ubuntu just because I never ran unity and wanted to check it out.

Thanks, 

Skip

---

### Post by Brandon_MacEachern on 2014-10-10
> **mechanic said:**
> Glad to see you fixed most problems in the end. But why change from xubuntu to the parent ubuntu/unity?

1.  Unity handles VSync better than Xfce (or should I say, XRender, or Compton).  For whatever reason, in Xfce, games do have dropped framerate if compositing is on, that is big.  In Unity it's not as bad, and the VSync is great.

2.  When using Photoshop CS in WINE, on Xfce it seems to not work well.  I can't move the tool windows around, and it tends to freeze up badly.  On Unity, this doesn't happen at all, works just fine.

3.  Xfce on my laptop just can't sleep right.  Light locker sucks.   I'm sorry, it does, it's garbage.  But even uninstalling it won't get around a particular bug I am experiencing.  When closing the lid to my laptop, in light locker, it wakes to a black screen, and you can't recover.  Without light locker, I have no mouse cursor and have to go to TTY1 and back to TTY7 every time I wake it up.  This just doesn't happen in Unity.  There's already a bug report.

4.  Xfce blacks out my keyboards backlight and has no way to enable it.  Unity it's built in.

5.  On video games, Xfce seems to have a problem where keys get stuck and I end up "auto moving" in one direction until I hit the key of that direction, like a key is stuck.  It's not sticky keys, and I don't have time to screw around with it.  Unity it doesn't do this.

So yea, those are my reasons.

---

