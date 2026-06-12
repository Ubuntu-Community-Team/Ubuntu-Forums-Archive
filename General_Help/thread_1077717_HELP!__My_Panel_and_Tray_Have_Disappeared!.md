---
title: "HELP!  My Panel and Tray Have Disappeared!"
date: 2009-02-22
forum: General Help
---

### Post by ram2008 on 2009-02-22
****This morning when I booted Ubuntu (8.04) I was startled to see that the panel and tray had disappeared!  Everything was fine when I was using it last night.  Right now I have no access to the main menu or any other system functions, just to a couple of programs that have icons on the desktop, one of which is the terminal.  At least with that I can reboot the system or do a total shutdown, all of which I've tried.  But the problem remains.  I'm quite new to Ubuntu so I'm at a loss as to what to do.  Would appreciate any suggestions.

---

### Post by whoop on 2009-02-22
So, did you lose both panels? If there still is a panel you can add a panel by right clicking the panel and selecting "new panel". Then you can add items to the panel by right clicking and selecting "Add to panel".

---

### Post by jpeddicord on 2009-02-22
In the terminal, type:

```
gnome-panel &
```

If you see the panels launch, type "exit" to close (do not click on the X as the panels will simply disappear again). If they do not start or you get an error, copy and paste it here. :)

---

### Post by ram2008 on 2009-02-22
****Hi guys,

And thanks for your replies.  Yes, I had lost both panels.  However, with your info, Jacob, I got both panels back.  I first had to install gnome-panel.  Wasn't installed.  Anyway I got both panels back with everything that I had added.  So I was happy about that.  However, I did get four error messages about four different panel apps as shown below.

*The panel encountered a problem while loading GNOME_FastUserSwitchApplet *.  It repeated the same message for Panel_TrashApplet, MixerApplet, and MultiloadApplet.  I had the option to keep them or remove them from my configuration.  For now I've opted to keep them and see what happens.  Any ideas as to what caused this?  Thanks again for your prompt response.  It was really appreciated.

---

### Post by jpeddicord on 2009-02-22
If gnome-panel was uninstalled, you may want to make sure that you still have the ubuntu-desktop package installed, as that ensures that your system stays usable and up-to-date between Ubuntu releases.

The applet problems are probably related; installing ubuntu-desktop may fix that. If it doesn't, just opt to remove them and re-add them via the right-click menu on a blank spot on the panel.

---

### Post by jimmybarcelona on 2009-02-25
I had both of my panels disappear as well, but in xubuntu. what packages should I be searching for in that distro. Would it be xubuntu-desktop?

---

### Post by mb_webguy on 2009-02-25
> **jimmybarcelona said:**
> I had both of my panels disappear as well, but in xubuntu. what packages should I be searching for in that distro. Would it be xubuntu-desktop?

Yep.  Try reinstalling the xubuntu-desktop package.

---

### Post by jimmybarcelona on 2009-02-26
Tried sudo apt-get install --reinstall xubuntu-desktop. and rebooted. still no panels. It's weird. When you right click on the desktop, the main applications menu shows up, rather than the option to create a new launcher, file, or folder. So the computer is still completely useable, I just don't understand what happened...

---

### Post by erwinsoo on 2010-07-10
> **ram2008 said:**
> ****This morning when I booted Ubuntu (8.04) I was startled to see that the panel and tray had disappeared!  Everything was fine when I was using it last night.  Right now I have no access to the main menu or any other system functions, just to a couple of programs that have icons on the desktop, one of which is the terminal.  At least with that I can reboot the system or do a total shutdown, all of which I've tried.  But the problem remains.  I'm quite new to Ubuntu so I'm at a loss as to what to do.  Would appreciate any suggestions.

press alt F2 and type xfce4-panel. Hit enter

---

