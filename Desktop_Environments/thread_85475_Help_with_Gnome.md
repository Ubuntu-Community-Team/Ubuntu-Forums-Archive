---
title: "Help with Gnome"
date: 2005-11-02
forum: Desktop Environments
---

### Post by scpike on 2005-11-02
So I installed breezy a few weeks ago, and everything has been working fine.  I also instaled kde/kubuntu-desktop packages, so that I can pick between kde and gnome at the splash screen.  
That all worked and everything was fine, but now a few weeks later when I try to log into gnome it just freezes at a brown screen, while constantly reloading the gnome-panel.  I can't right click on the desktop/ everythin is unresponsive.  KDE is working fine...  any help on how I can reset the gnome settings/ can i reinstall all of gnome/ubuntu-desktop somehow?

Thanks

---

### Post by iH8forcedRegistration on 2005-11-02
you might consider 'hiding' your gnome configuration files and seeing whether that helps.

Open a terminal when not running Gnome (from KDE or better yet a failsafe terminal) and type this:
```

cd ~
mv .gnome .gnome.old
mv .gnome2 .gnome2.old
mv .gnome2_private .gnome2_private.old
mv .gnome_private .gnome_private.old
mv .gtkrc-1.2-gnome2 .gtkrc-1.2-gnome2.old
mv .gtkrc-2.0 .gtkrc-2.0.old

```

That will effectively prevent gnome from finding any of its configuration files next time you try to start it, and it'll then try to rebuild them. And, if that doesn't work, you can always get your configuration back by renaming the .old files back the way they were.

---

### Post by scpike on 2005-11-02
thanks that worked perfect

---

