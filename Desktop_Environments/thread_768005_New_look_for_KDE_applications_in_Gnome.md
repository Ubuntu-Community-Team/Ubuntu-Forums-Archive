---
title: "New look for KDE applications in Gnome"
date: 2008-04-26
forum: Desktop Environments
---

### Post by Kuzja on 2008-04-26
I am sure that there has been tons of threads like that before, but i decided to make my humble contribution to this awesome community and share with you how i made KDE applications look better in Gnome.

In my work I used  following guides:
[http://jacekfurmankiewicz.blogspot.com/2007/05/integrating-kde-applications-into.html](http://jacekfurmankiewicz.blogspot.com/2007/05/integrating-kde-applications-into.html)
[http://thedarkmaster.wordpress.com/2007/07/03/kde-applications-looking-bad-in-gnome-lets-fix-em-up/](http://thedarkmaster.wordpress.com/2007/07/03/kde-applications-looking-bad-in-gnome-lets-fix-em-up/)
and also some files from here:
[http://www.kde-look.org/content/show.php/Ubuntu+Human+Cookies+Mod?content=58644](http://www.kde-look.org/content/show.php/Ubuntu+Human+Cookies+Mod?content=58644) (which is basically a set of stuff to make Kubuntu look like Ubuntu)

So, you want to start with getting kcontrol. Execute the following command in your terminal:

> sudo apt-get install kcontrol

Then you can open it using

> kcontrol

The first thing you should do is navigate to Fonts menu and change fonts to a more Gnome-like:
[[IMG]http://img512.imageshack.us/img512/3340/fontsuy8.th.png[/IMG]](http://img512.imageshack.us/my.php?image=fontsuy8.png)

Then download files from here the following sources:
[http://kde-look.org/content/show.php/Human_KDE+Mod.+-Form.+HumanKDEKanpio+Mod?content=58968](http://kde-look.org/content/show.php/Human_KDE+Mod.+-Form.+HumanKDEKanpio+Mod?content=58968) ( you need both archives)
[http://kde-look.org/content/show.php/Kubuntu+Human+Theme?content=42746//](http://kde-look.org/content/show.php/Kubuntu+Human+Theme?content=42746//)
[http://kde-look.org/content/show.php/Human+(Dapper)?content=39402](http://kde-look.org/content/show.php/Human+(Dapper)?content=39402) (copy this to a text file and save it with extension .kcsrc)


and use them to alter color scheme, theme and icons:
.kcsrc for colors
bctangokde_07.tar.gz and Human_kde.tar.gz for icons ( note that both should be installed but you need to choose Human_kde as your icon theme)
42746-Kubuntu Human.kth for theme

That's it! You are good to go! I normally use Amarok and Ktorrent and both look really great now. I would say that they are even nicer then some native GTK applications.

[[IMG]http://img410.imageshack.us/img410/9554/ktorrentxs8.th.png[/IMG]](http://img410.imageshack.us/my.php?image=ktorrentxs8.png)

[[IMG]http://img91.imageshack.us/img91/6676/amarokms4.th.png[/IMG]](http://img91.imageshack.us/my.php?image=amarokms4.png)

PS. I hope someone will find this mini-guide helpful

---

### Post by Kuzja on 2008-04-26
I've also noticed that other QT-based third-party applications like Skype or aMule get a better look with this one.

---

