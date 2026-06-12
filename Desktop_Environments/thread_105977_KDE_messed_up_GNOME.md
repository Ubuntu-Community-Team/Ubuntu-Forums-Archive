---
title: "KDE messed up GNOME"
date: 2005-12-19
forum: Desktop Environments
---

### Post by bjtuna on 2005-12-19
I'm running Breezy, been running the default gnome installation for a while, no major problems. Today I felt like giving KDE a whirl so I installed 'kubuntu-desktop', logged out, and logged back in by choosing KDE from the GDM screen.  I kicked around in KDE for a while, messed with the themes (including the settings of how to theme GTK apps) and decided to go back to GNOME. I went into GNOME and now the themes are wacky. As an example, when I mouseover a button widget, there's a weird blue border around the button.   Also, when I tried switching themes around in GNOME, my clock applet died.

---

### Post by wounded on 2005-12-19
I had the same problem.

I had Gnome and KDE along side each other running great for a long time. I then decided to backup my /home and reinstall mounting the base and /home on separate partitions. After I did this everything was nice. I installed KDE again, no problems. Then a few days ago I decided to mess around with KDE.

I had been in it before but this was the first time I had messed with settings and such to make it look how I liked (Why is it so cartoony by default? :P ). so i mess with wallpapaer, the panel, default fonts and stuff. Then I go back into gnome and shortly afterwards my clock crashed and i then couldnt start new applications. I reinstall of my base system did the exact same thing the moment after I installed KDE. But even after reinstalling my base and deleting both gnome and KDE settings folders in /home I still am not running smoothly as i have before.

When I had deleted my hidden Gnome folders things were working (I could get into Gnome then) but quickly went bad soon after.

As far as I can tell the only thing that could have been the problem, in my case, is the KDE settings folders I think. Seeing as how both of us started these problems after messing with KDE too :( I would suggest deleting .KDE or atleast renaming it for now and then see if that helps your Gnome install. Or you could just use KDE now :S

---

### Post by bjtuna on 2005-12-19
Ok the quick answer is that I had to wipe out ~/.gtkrc-2.0 as per this thread:

[http://www.ubuntuforums.org/showthread.php?t=58787&highlight=kde+gnome+theme](http://www.ubuntuforums.org/showthread.php?t=58787&highlight=kde+gnome+theme)

But I'm assuming that if I fired KDE back up, it would screw things back up again.

---

