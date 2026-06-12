---
title: "Nautilus Back/Forward mouse functionality"
date: 2008-08-21
forum: Desktop Environments
---

### Post by Kimeras on 2008-08-21
Ubuntu 8.04

I was happy that the forward and back functionality had been fixed or added? to Firefox recently. The last time i tried Ubuntu i had to try modifying the xorg.conf file for a 5 button mouse in order to get this working. 

I don't even remember if it did work in the end, that was quite some time back. I didn't even know that you had to be root to edit certain files, or even how to do this. 

I do now and sudo gedit is my friend ;P

I've looked high and low for some way to get back/forward mouse button functionality in Nautilus and I've tried quite a few things.

I've found guides on how to get this to work on the LG5 mouse or the [IMWheel]("http://ubuntu-tutorials.com/2006/12/02/imwheel-5-button-mouse-within-nautilus-ubuntu-610/") just for starters. 

They all seem to say the same thing which is just more editing of the xorg.conf. I've tried a few setups but this time round i actually loose functionality eg. in Firefox the back and forward buttons stop working.

Searching has also been distinctly hard, i find it hard to dredge up the information i need. I don't know if this is just because it doesn't bother people as much as me or whether the options for a solution are in fact sparse. 

Either way i decided to try my luck with you guys.

So, how does one get the back and forward functionality in Nautilus with a bog-standard 5 button mouse?

---

### Post by Kimeras on 2008-08-22
bump

---

### Post by maniheer on 2008-08-23
If you have it working in Firefox then all you have to do is to open Nautilus

Go to Edit>Preferences and go to the behaviour tab. And select Always open browser windows (or similar)

If it never worked in Firefox then visit [http://thetechforums.net/howToLinux/?p=6](http://thetechforums.net/howToLinux/?p=6)

Hope I helped

---

### Post by Kimeras on 2008-08-24
Thanks for the info, i followed it up and decided to use another approach in case this was outdated (current using hardy 8.04).

I did find a solution to this and i think it could help many others solve this problem :)

By default it seems, at least for my install, that xorg.conf is setup to run a bog-standard 3-button (scroll) mouse without any bells and whistles. Firefox (3.0) must have been using its own work around to detect a 5/7 button mouse to add back/forward functionality.

If your mouse has back and forward buttons its likely that it uses the intellimouse implementation in which case the imwheel (intellimouse) package will have to be installed and a few minor adjustments made to the xorg.conf in order to get this working. 

```
sudo aptitude install imwheel
```
(This also seems to remove a massive amount of packages, I don't really know why)

Following this guide should get it all working nicely for you :) its the first thats worked and actually provided proper support for back/forward buttons throughout Ubuntu 8.04.

[http://ubuntuforums.org/showthread.php?p=2398239]("http://ubuntuforums.org/showthread.php?p=2398239")

---

