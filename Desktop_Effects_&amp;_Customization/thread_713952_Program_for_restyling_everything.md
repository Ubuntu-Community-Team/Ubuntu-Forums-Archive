---
title: "Program for restyling everything"
date: 2008-03-03
forum: Desktop Effects &amp; Customization
---

### Post by Jadd on 2008-03-03
A while ago, I asked the Ubuntu forums community for a [restyling program](http://ubuntuforums.org/showthread.php?t=635269). It just occured to me that this is the place I should be asking.
What I'm looking for is a program that can restyle your entire OS automatically, including:
[LIST]
[*]GTK themes (controls)
[*]Metacity themes (window borders)
[*]Emerald themes (compiz window borders)
[*]Grub screens (booting up screen)
[*]Splash screens
[*]Login themes (GDM)
[*]Mouse cursors
[*]Icon sets
[*]Wallpaper
[*]Qt themes (KDE app's controls)
[*]AWN
[*]...
[/LIST]

A lot of other people seem to want this, according to [this thread](http://ubuntuforums.org/showthread.php?t=635269), [this brainstorm idea](http://brainstorm.ubuntu.com/idea/105/), and [this blueprint](http://www.gtk-apps.org/content/show.php/Desktop+Designer?content=75860&PHPSESSID=900bbd30d070d45471cb54a0b4254835).

So, seeing this hasn't been done before, I propose we try it. There are several ways we could do it:
[LIST]
[*]**Use debian packages**, like [this one](http://ubuntuforums.org/showpost.php?p=3946417&postcount=11). Thanks Hairy_Palms! We could have a package, say totally_green, that depends on other packages (a metacity one, an icon set one, etc), that runs a script to enable them all. The advantages of this system is that several schemes can share dependencies and reduce unneccessary downloads and installation, uninstallation and upgrading is fairly simple. The drawbacks include confusing themes with actual programs, and having to code and include a script in every scheme package.
[*]**Invent a new system of repositories** for the .tar.gz that include any kind of themes to keep the benefits of the deb system while keeping themes and programs seperate.
[*]Use a GUI program in **wizard form**, like this. I've already coded a prototype with some functionality which you can download at:
[http://www.4shared.com/dir/5288885/4089e83e/complete-look.html](http://www.4shared.com/dir/5288885/4089e83e/complete-look.html)

[[img]http://ubuntuforums.org/attachment.php?attachmentid=61460&stc=1&thumb=1&d=1204557724[/img]](http://ubuntuforums.org/attachment.php?attachmentid=61460&d=1204557724)[[img]http://ubuntuforums.org/attachment.php?attachmentid=61461&stc=1&thumb=1&d=1204557724[/img]](http://ubuntuforums.org/attachment.php?attachmentid=61461&d=1204557724)

[*]Use a program that **gathers all theming options**, and includes the ability to mix and match, and save schemes. DBGthekafu has coded a prototype but with no functionality which you can get at
[http://www.gtk-apps.org/content/show.php/show.php?content=75860&vote=good&tan=1393450&PHPSESSID=900bbd30d070d45471cb54a0b4254835](http://www.gtk-apps.org/content/show.php/show.php?content=75860&vote=good&tan=1393450&PHPSESSID=900bbd30d070d45471cb54a0b4254835)

[[img]http://ubuntuforums.org/attachment.php?attachmentid=61462&stc=1&thumb=1&d=1204557724[/img]](http://ubuntuforums.org/attachment.php?attachmentid=61462&d=1204557724)

[/LIST]

So two questions: has this been done before? What's the best way of doing it?

It should be possible to make a complete-look/theme/scheme and save it, including the data files, so that you can share them with other people and computers, just like snorpey wanted when he/she posted his/her idea. By the way, if you like the idea, go and [vote for it](http://brainstorm.ubuntu.com/idea/105/)!

[[IMG]http://brainstorm.ubuntu.com/idea/105/image/2/[/IMG]](http://brainstorm.ubuntu.com/idea/105/)

---

### Post by Jadd on 2008-03-04
I just realised this Desktop Effects & Customization section falls under Main Support Categories. I'm not looking for support, I'm looking for a brainstorming discussion. Is there a better category than this one?

---

### Post by jdsony on 2008-03-04
I agree. It seems silly that there are separate programs that take care of each piece of the OS look. Once you get it how you like it, it's ok but it is a bit of a pain to get to that point.

---

### Post by dbg on 2008-03-05
I would prefer a GUI which include everything to style my desktop!
For now I must open 9 Gui's when I want want to give my desktop a new uniform control interface. Also for some kind of stuff, like the splash screen there is no GUI to change it manually. A single gui like the “Desktop Designer” would this make very easy. When everything would work I imagine, you could customize the :

Wallpaper, the positions of the applets, a dock, your curser style, the sound, widgets, the screensaver
the window border, GTK theme, icon theme, Fonts, Window effects theme (compiz)
Grub, Usplash, GDM, Splash screen
and program themes like the Firefox, to get a better integration in the desktop style

with just one gui!!! I know this would need much time and work of programming, but the result would be that it would not be necessary anymore to search for the app you need when you wants to change something and it would clean up the Preferences and the administration menu a little bit. To save all settings in one desktop Theme it would make very easy to change and share the whole desktop style very fast.

I think the advantage of a gui like the desktop is the simpleness to change, share and to make a desktop theme. It would be as simple as to change the icons, gtk etc. for now with the Applications control panel,with also the possibility to change the downloaded desktop theme very simply and of course that you have everything under one gui.

The other ideas ( the wizard and the debian package) have the advantage, that they would be simpler to program and are also very easy to use. You just need to install the debian package and the desktop looks great, if it was designed by a good artist. But the great disadvantage would be the creation of the package. The desktop designer would be able to save the active settings, the other ones needs a artist who creates them.

---

### Post by Flimm on 2008-05-10
I've started a python project on this, it's hosted on launchpad:
[https://launchpad.net/complete-look/](https://launchpad.net/complete-look/)
(Yes, I borrowed the name complete-look, I hope you don't mind, I'm planning to change it anyways.)
Currently, it does activate schemes (wallpaper, gtk, icons, metacity, usplash, grub, gdm) all at once, but the installation process has yet to be coded. The pre-alpha release contains a README.txt file that you should read if you want to test this.
Just to let you know that some-one is working on this!

---

