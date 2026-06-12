---
title: "gnome problem when installing aiglx + compiz on kubuntu"
date: 2006-07-22
forum: Desktop Environments
---

### Post by bakinsoda on 2006-07-22
Hi all,

I was trying to install aiglx + compiz on kubuntu 6.06 on my dell 700m to get that 3d desktop switch thing (want to try it out and make others jealous!).

Well, I was following the instructions of http://www.ubuntuforums.org/showthread.php?t=145068&highlight=aiglx+compiz

up until before step 3, configure gdm, since i dont use gnome.

Then i followed http://www.ubuntuforums.org/showthread.php?t=216543&highlight=aiglx+compiz

to set it up for KDE.

When i reboot, kubuntu starts up.  When X starts, i get this black and white fuzzy thing.  Then the kubuntu screen pops up.  I sign on, then theres this "Gnome window" popping up, and it just stops there.  I can't do anything.  clicking gets rid of this "Gnome window," but then i get a black screen with a mouse cursor.  Nothing else.

I know i screwed up big time.  I booted into console and undo what i did in the previous two threads, but this gnome window still appears after i log into kubuntu.

Does anyone know how i can get rid of this so i can go back to my normal KDE desktop.  Please help as i just migrated over to linux and have been loving it.  I don't want to call it quits on linux just because of this.

I'm guessing i need to change some kind of start up sequences?  I don't know where the gnome came from, maybe the compiz-gnome stuff?

THANKS ALL

---

### Post by mainstreetexile on 2006-08-10
i'm having the same exact problem, I restored my original xorg.conf, /etc/environment and /etc/kde3/kdm/kdmrc files and uninstalled compiz-gnome via aptitude but it still boots into gnome "window manager" after the kde login screen.

did you have any luck fixing this?

---

### Post by bakinsoda on 2006-08-10
I did fix this problem.  I realized that aiglx and compiz stuff was trying to boot up as a gnome desktop, so when i booted up (i have a boot menu), i went down to the "safe mode" equivalent of kubuntu, which is command line based.  mine had internet connection, so i apt-get install gnome (i think it is gnome-desktop-environment), and then i restarted.  Regular boot took me to a gnome environment.  To change to kde again, at the login screen, there should be one of two buttons that allow u to choose the desktop enviroment (not session button but the other one).

Let me know if its not clear enough.

---

