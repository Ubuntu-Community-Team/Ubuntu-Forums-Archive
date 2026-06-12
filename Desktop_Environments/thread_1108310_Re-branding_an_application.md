---
title: "Re-branding an application?"
date: 2009-03-27
forum: Desktop Environments
---

### Post by fredbird67 on 2009-03-27
I've been tinkering with the idea of creating my own Linux distribution based on Ubuntu.  I've been weighing a lot of options regarding what menu system to use on GNOME, and have decided that I like MintMenu the best.

However, I'd like to rename and rebrand that package if at all possible.  I have no plans at all to charge for it or anything, it's just that I want my proposed name for it and its logo to stick out and be foremost in people's minds when using it.  Of course, I have other things in mind to include in it that will hopefully set my distro idea apart if it ever sees the light of day.

Thanx in advance,
Fred in St. Louis

PS -- I don't have anything against Linux Mint or anything.  I've checked it out, and I consider it to be an excellent distro.  In fact, I plan to include a couple of nice touches Clem has included in Mint, such as setting Firefox so that pressing the backspace key does the same thing as the back button, and having a red background on Nautilus when opened with the sudo or gksudo prefix, both of which I know how to do on my own.  However, I'm not going to include any tools unique to Mint or anything, as I plan to keep this very much Ubuntu-based, with those three ideas from Mint thrown in.

---

### Post by Mulenmar on 2009-03-27
*bump* I'd like to know about this as well, we wouldn't want another Mozilla vs Debian type fiasco.

---

### Post by VeeDubb on 2009-03-27
It is my understanding that anything released under GLP/GNU licensing can be modified and redistributed to your hearts content with only 2 restrictions.

1. You must give credit where credit is due.  i.e. you can't slap some lipstick on mintmenu and claim that it was all your work.

2. Anything you modify and distribute, you must share all appropriate source code and resources.

---

### Post by 3Miro on 2009-03-27
I hope you have considered the sheer amount of work it would be to redo the repositories. If your .deb files have something other than ubuntu in their names, then you will run into trouble.

Otherwise it would be Ubuntu with a different default desktop settings (even the desktop environment would be the same).

I guess you can do that, but I kind of fail to see the general point. I guess you can just make a script that runs on Ubuntu post-install and makes the changes to .gnome and whatever else.

There shouldn't be any legal issues as long as you clearly state what you are doing.

---

### Post by joey-elijah on 2009-03-27
I have to agree about re-branding etc - are you just going to change the names in the menu or get down and dirty changing any icons or naming schemes present in the applications themselves. The first one does not a distro make, the second one has more of a point.

Although i'm not here to discourage anyone from starting a distro, it's worth looking around at other smaller Ubuntu forks (such as mint) and seeing whether you're offering anything different bar a GTK theme, wallpaper and colour scheme. If not then why not just package your "branding" up into something you can distribute on gnome-look - you'll save yourself many a headache! 

There are plenty of pseduo-distro's out there that pretty much are just ubuntu with a lick of paint and it'd be easier for a user to just grab said theme and install it themselves rather than downloading a 700MB .iso and having to reinstall/partition. 

Mint has a unqiue image, but it also packages up many things Ubuntu cannot ship with because of it's position (codecs).
gOS takes this further still by adding certain packages, software and UI tweaks that others don't.

Maintaining packages/repos etc for "rebranded" software is a lot of effort. 

When i look at distro's i look for ease of use, uniquness, software packages, DTE and stabilty etc far above 'branding'.

---

