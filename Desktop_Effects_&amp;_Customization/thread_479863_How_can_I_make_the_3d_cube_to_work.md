---
title: "How can I make the 3d cube to work?"
date: 2007-06-20
forum: Desktop Effects &amp; Customization
---

### Post by jltp18 on 2007-06-20
I installed beryl like 2 hours ago, and everything was ok, I had the 3d cube and all the efects, then something happened and suddenly I didnt had taskbars, I fixed it, but now I cant make the 3d cube to work, I type ctrl+alt+click and nothing happens, and in beryl the 3d cube option is enabled, also when I changed enviroments, no effect takes place, only the a new desktop appears, can somebody help me please?

---

### Post by jgcamp99 on 2007-06-20
> **jltp18 said:**
> I installed beryl like 2 hours ago, and everything was ok, I had the 3d cube and all the efects, then something happened and suddenly I didnt had taskbars, I fixed it, but now I cant make the 3d cube to work, I type ctrl+alt+click and nothing happens, and in beryl the 3d cube option is enabled, also when I changed enviroments, no effect takes place, only the a new desktop appears, can somebody help me please?

I'm running an ATi 9600XT 256 MB video card. Using the latest kernel with updates and really just a default install (no fglrx) mesa. I get the desktop effects to work under system preferences. Wobbly effect and 3d cube. With mine the desktop is a full window cube effect, Workspaces is set for preferences to be 1 row, 1 workspace. The resultant workspaces icon on the bottom panel shows 4 workspaces. I can drag open applications to the edges of the screen and the application moves effortlessly to the next workspace of the cube and the entire fullscreen is a cube effect. I don't know what Beryl gives anyone in addition, but I'm pleased with what mesa and the desktop effects enabled provides. To be honest, I prefer this to seeing a cube on the desktop. Oh, and simultaneous alt,  ctrl left, right up and down displays the next workspace of the cube. As well, the problem you indicate no panels or taskbars, that doesn't happen, all workspaces have the same menu and panels, so I can open up new applications there, even drag them to other workspaces that have applications open there or a new blank workspace with the menu and panels.

---

### Post by jgcamp99 on 2007-06-21
Took a chance and sudo apt get beryl and now I see where Beryl has even more features. I'm impressed with Ubuntu.

---

### Post by SendDerek on 2007-06-21
There would've been two ways to fix it:

1.)  In the configuration editor there is a section for compiz.  I usually search for hsize using the "find" utility and then make sure it's set to 4 and not 1.

2.)  Download gnome-compiz-manager and set the workspaces to 4 in the "Windows" tab.

Apparently, this exact problem is happening to a lot of people, including me.  Hopefully it will be fixed sometime soon.

---

### Post by jgcamp99 on 2007-06-23
And as far as my few days with Beryl, it seems to me that initially there are boots from being completely shut down that Beryl will crash. This is evident that in the Beryl Manager, that an option to load an alternate (fall-back) window and window manager that is by default Gnome's metacity.

I believe and for no reason I can come up with logically, that Beryl is more stable at boot last night and today thus far. I have reset the settings to utilize all features of Beryl, that is without getting a message that tells me what box I checked off on doesn't conflict with another feature.

Like anything freshly installed, I expect a few quirks but after a couple days with Beryl, the quirks seem to have ironed themselves out. My progression, since 7.04 introduced, I stayed with Mesa drivers for the ATi video card. Subsequent updates over the past couple months and I then became bold enough to enable desktop effects and since I did nothing more than enable them after normal updates that included every repository the Ubuntu offers, I'm certain that what I had that produced wobbly and 3d cube was simply Mesa with Compiz. Then a couple days ago, I followed Ubuntu's how to for beryl (it's really this same procedure in the link below):

[http://wiki.beryl-project.org/wiki/Support_for_ATI_cards](http://wiki.beryl-project.org/wiki/Support_for_ATI_cards)

when I checked for direct rendering, mine was capable, so the install of additional driver wasn't necessary for me.

BTW, as of this point in time, I suggest enabling Ubuntu's repositories for restricted modules right after you install Ubuntu period, it's the only way to get the absolute most and best from/out of Ubuntu. Ubuntu is pretty darn good with the packages they offer thru the entire multitude of repositories as a whole. And outside of seeing the different ones, can only explain it as necessary for cutting edge or simply expermental stuff anyway.

---

