---
title: "Fedora boot loading screen?"
date: 2008-01-08
forum: Fedora/RedHat and derivatives
---

### Post by Romanus81 on 2008-01-08
I tried installing fedora, but it just gave me a headache of problems and grub wouldn't install. I did see a few features that I liked, such as the screen with the progress bar that fedora 8 boots with. The problem with the one Ubuntu uses is that it is stretched and ugly on a 1440x900 monitor. Does fedora use a different boot loader program? Is it possible for me to get it working in ubuntu?
If I ever work out the install problems, I will try out Fedora more fully.

---

### Post by igknighted on 2008-01-10
> **Romanus81 said:**
> I tried installing fedora, but it just gave me a headache of problems and grub wouldn't install. I did see a few features that I liked, such as the screen with the progress bar that fedora 8 boots with. The problem with the one Ubuntu uses is that it is stretched and ugly on a 1440x900 monitor. Does fedora use a different boot loader program? Is it possible for me to get it working in ubuntu?
If I ever work out the install problems, I will try out Fedora more fully.

Ubuntu uses "usplash", which I believe is a boot-splash program created specifically for Ubuntu.  You can change the resolution of the splash in Ubuntu (default is 1024x768 IIRC), but I do not think that it is capable of wide-screen aspect ratios (16:9/16:10), only the standard 4:3.

Fedora, on the other hand, uses rhgb (Red Hat Graphical Boot... clever huh?).  This works very differently.  Where as Ubuntu's splash screen is just an image displayed, rhgb actually loads an xserver to display the splash screen.  Hence you have a mouse and the ability to interact (all you can do is click details though).  This is also why you see a few seconds of text in the beginning of the Fedora boot sequence, because the xserver hasn't been loaded yet.

Each of these has its pluses and minuses.  I think that Fedora's is more powerful, but Ubuntu's is simpler.  A solution you might want to consider is this:  Take an image in the aspect ratio you want (1440x900 in your case), and squish it horizontally with GIMP (to a 4:3).  Then save the file and point usplash to the new file.  Now when it distorts the file, it should distort it to the proper ratio.  This could totally bomb and be grainy because the pixels have moved and dont fit the screen, but it might be worth a shot.

---

### Post by vincentvee on 2008-01-14
how do you point usplash to it?
i remember in 6.06 there was a gui tool you could ude to change the usplash images, but i cant find it for 7.10
any ideas? i cant even remember the name of the app...

UPDATE: found the program, it's here: [http://getdeb.net/download.php?release=917&fpos=0](http://getdeb.net/download.php?release=917&fpos=0)
> **igknighted said:**
> 
Fedora, on the other hand, uses rhgb (Red Hat Graphical Boot... clever huh?).  This works very differently.  Where as Ubuntu's splash screen is just an image displayed, rhgb actually loads an xserver to display the splash screen.  Hence you have a mouse and the ability to interact (all you can do is click details though).  This is also why you see a few seconds of text in the beginning of the Fedora boot sequence, because the xserver hasn't been loaded yet.


---

