---
title: "Window Tiling"
date: 2009-04-27
forum: Desktop Environments
---

### Post by mahasmb on 2009-04-27
Like many people, one of the few things I miss from Windows is being able to actually tile windows horizontally/vertically.

1.) I tried the unsupported Compiz-Fusion plugin for tiling. It DID NOT WORK. I would check mark it in Compiz Config Settings Manager, and it would just check mark itself off. I tried this over and over.

2.) I've read up on separate window tiling managers, but apparently a few of these require that I give up Gnome... (i.e. "Awesome", "Xmonad", etc). I really don't think I should have to do that just to be able to tile windows... ridiculous really. Plus, I don't want to give up Gnome. I've got it working and looking exactly as I want it to. I am, of course, also aware that there's an option to use something like Xmonad with Gnome, but then I'd have to give up Metacity... once again, same issue.

3.) So I landed on this tutorial: [http://ubuntuforums.org/showthread.php?t=470160&page=2](http://ubuntuforums.org/showthread.php?t=470160&page=2)

It actually works, and with little configuration. It just doesn't work very well... Although I can actually tile horizontally/vertically for some strange reason my Gnome panels get moved around as well. OF COURSE, I don't want this. I've tried to lock the panels with gconf-editor, but that still doesn't help. Here's a picture to demonstrate:


[IMG]http://img.photobucket.com/albums/v185/SakuraFanelia/Screenshot-3.png[/IMG]

Has anyone had this problem? Any ideas.

I'm using Jaunty Jackalope

---

### Post by mahasmb on 2009-05-01
No ideas? :(

---

### Post by bloodchilde on 2009-05-05
The new compiz fusion unsupported plugins package, v0.8.2 is not yet included in Ubuntu repositories for some reason. Remove old package and install this one:

[http://philip.magicalforest.se/pool/hardy/compiz/compiz-fusion-plugins-unsupported_0.8.2-hardy~ppa1_i386.deb](http://philip.magicalforest.se/pool/hardy/compiz/compiz-fusion-plugins-unsupported_0.8.2-hardy~ppa1_i386.deb)

(yes, i know it says "hardy", but it works fine in my Jaunty ;) )

---

### Post by JK3mp on 2009-05-05
Compiz always has alot of issue's not entireley worked out. What would be the huge prolem with giving up metacity? I believe u can maintain your metacity theme window by default with awesome...but i havn't used it personally...and there's always a bunch of choices for window decor in every window manager. Not to mention you can always design one yourself... ;)

---

### Post by mahasmb on 2009-05-25
> **bloodchilde said:**
> The new compiz fusion unsupported plugins package, v0.8.2 is not yet included in Ubuntu repositories for some reason. Remove old package and install this one:

[http://philip.magicalforest.se/pool/hardy/compiz/compiz-fusion-plugins-unsupported_0.8.2-hardy~ppa1_i386.deb](http://philip.magicalforest.se/pool/hardy/compiz/compiz-fusion-plugins-unsupported_0.8.2-hardy~ppa1_i386.deb)

(yes, i know it says "hardy", but it works fine in my Jaunty ;) )

It works like a charm! This is the first time I've got window tiling working in Ubuntu since I started using Ubuntu all the way back in the Dapper days.

Thanks a bunch.

---

