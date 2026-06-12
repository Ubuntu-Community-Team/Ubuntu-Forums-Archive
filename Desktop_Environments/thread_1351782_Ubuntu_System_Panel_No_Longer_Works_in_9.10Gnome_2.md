---
title: "Ubuntu System Panel No Longer Works in 9.10/Gnome 2.28"
date: 2009-12-10
forum: Desktop Environments
---

### Post by beastrace91 on 2009-12-10
So after using Linux Mint for a few weeks one thing I really grew accustomed to was they awesome Mint Menu - Ubuntu has one like it called the "Ubuntu System Panel" and I was always able to build it following the instructions [here](http://code.google.com/p/ubuntu-system-panel/wiki/Installation). However since I recently formatted to 9.10 (and thusly Gnome 2.28) it no longer adds properly - the applet promptly crashes out on me when ever I try to load it up :-/

Any have any suggestions for how I might be able to get it working? It really is a must have for my system at this point - the default Gnome menu is bland at best, but I like alot of the other Gnome features so I am bear to swap over to KDE.

Regards,
~Jeff

---

### Post by m2xtreme on 2010-03-19
I have the same problem trying to get USP to work.  I take it you installed from Karmic 9.10 and didn't update from Jaunty 9.04?  Hopefully by Lucid it will have fixed itself... until then I'll keep looking for an answer.

---

### Post by beastrace91 on 2010-03-19
> **m2xtreme said:**
> I have the same problem trying to get USP to work.  I take it you installed from Karmic 9.10 and didn't update from Jaunty 9.04?  Hopefully by Lucid it will have fixed itself... until then I'll keep looking for an answer.

The solution I went with was just installing Mint... This amoung other reasons makes it far better than Ubuntu.

~Jeff

---

### Post by Gemnoc on 2010-03-19
I don't know why you are not able to install Ubuntu-system-panel. I did it from the SVN a few weeks ago, under Karmic Netbook Remix.

But I went back to the MintMenu, it's better made, even if it's based on USP. The default USP install looks like crap, gigantic bold fonts are used everywhere, the result is most apps names and descriptions exceed the column widths, unless you're willing to set USP's window width at least 2/3 of your screen width. I gave up trying to understand how to configure it as there is no documentation provided.

You can add the Linux Mint repository in Karmic (sorry can't find the link ATM). Then you find and install the mintmenu package. Beware that it will need to install other packages as well. I couldn't find the authentification key to it, so I got errors that the packages were not from a secure source. Got the same error when doing system updates as well, so afterwards I disabled Mint's repo.

Another way would be to download the packages and install them manually as explained [here]("http://www.khattam.info/2009/08/01/install-linux-mint-menu-in-ubuntu/").

I was able to change the Mint Software Manager button to Ubuntu's Software Store by following the [How-to here]("http://ubuntuforums.org/showthread.php?t=1131845"). I still need to find out how to change its description. As for adding or removing favorite apps, it's simple: there's a file named applications.list in ~/.linuxmint/mintMenu that you can edit.

---

### Post by beastrace91 on 2010-03-20
> **Gemnoc said:**
> I don't know why you are not able to install Ubuntu-system-panel. I did it from the SVN a few weeks ago, under Karmic Netbook Remix.

But I went back to the MintMenu, it's better made, even if it's based on USP. The default USP install looks like crap, gigantic bold fonts are used everywhere, the result is most apps names and descriptions exceed the column widths, unless you're willing to set USP's window width at least 2/3 of your screen width. I gave up trying to understand how to configure it as there is no documentation provided.

You can add the Linux Mint repository in Karmic (sorry can't find the link ATM). Then you find and install the mintmenu package. Beware that it will need to install other packages as well. I couldn't find the authentification key to it, so I got errors that the packages were not from a secure source. Got the same error when doing system updates as well, so afterwards I disabled Mint's repo.

Another way would be to download the packages and install them manually as explained [here]("http://www.khattam.info/2009/08/01/install-linux-mint-menu-in-ubuntu/").

I was able to change the Mint Software Manager button to Ubuntu's Software Store by following the [How-to here]("http://ubuntuforums.org/showthread.php?t=1131845"). I still need to find out how to change its description. As for adding or removing favorite apps, it's simple: there's a file named applications.list in ~/.linuxmint/mintMenu that you can edit.

Why not just install Mint?...

~Jeff

---

### Post by Gemnoc on 2010-03-20
> **beastrace91 said:**
> Why not just install Mint?...

~Jeff
Duh. Because I already had Ubuntu installed? Because I like it as it is, apart from the menu*? Because Ubuntu has a bigger community (I'm mostly on the Ubuntu-fr forums, the French forum for Mint looks deserted by comparison)? Because if I'm going to do a reinstall, I'll install 10.04 which is just around the corner?

* BTW this was for my mini notebook, on which I've had UNR since the RC but tired of the home screen. On my desktop I have all the screen space I need for a top and a bottom panel (1920x1200 24-inch LCD), so I have the Ubuntu menu which I like just fine.

---

### Post by beastrace91 on 2010-03-20
Heh for 9 issues out of ten that occur on Mint you can post on the Ubuntu forums and get help for them. But to each their own, choice is the wonderful part about FOSS :)

~Jeff

---

### Post by m2xtreme on 2010-03-27
Mint isn't for me, I'll stick with Ubuntu.  As for USP, I'll just wait for Lucid to come out and give it another shot.  It's not that vital to me atm.

---

