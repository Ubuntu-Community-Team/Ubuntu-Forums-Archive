---
title: "Mac OS Style Menu Bar"
date: 2010-10-11
forum: Desktop Environments
---

### Post by trentscott on 2010-10-11
Is it possible to install the Mac OS-like menu bar in Ubuntu 10.10 desktop? I know it's in the Netbook remix but I haven't come across anything saying whether it can be installed (successfully) on the desktop edition.

---

### Post by ankspo71 on 2010-10-11
Hi,
Maybe these links will help.
[http://www.webupd8.org/2010/05/application-menu-global-menu-for-ubuntu.html](http://www.webupd8.org/2010/05/application-menu-global-menu-for-ubuntu.html)
Which links to this:
[https://edge.launchpad.net/~canonical-dx-team/+archive/une](https://edge.launchpad.net/~canonical-dx-team/+archive/une)
which shows it is available for both Lucid and Maverick.
This is the one that is in Ubuntu Netbook 10.10.

I also found this one:
[http://joesteiger.com/2010/06/14/install-global-menu-mac-os-x-like-panel-ubuntu-10-04/](http://joesteiger.com/2010/06/14/install-global-menu-mac-os-x-like-panel-ubuntu-10-04/)
Here is what it looks like:
[https://wiki.ubuntu.com/global_menu](https://wiki.ubuntu.com/global_menu)
Hope this helps.

(Borrowed from my other replies at [http://ubuntuforums.org/showthread.php?t=1592838](http://ubuntuforums.org/showthread.php?t=1592838))

---

### Post by wiebeest on 2010-10-11
> **trentscott said:**
> Is it possible to install the Mac OS-like menu bar in Ubuntu 10.10 desktop? I know it's in the Netbook remix but I haven't come across anything saying whether it can be installed (successfully) on the desktop edition.

There allready was global menu, available from here:[**global menu -link**]("http://code.google.com/p/gnome2-globalmenu/")

The netbook remix version is called **Indicator Applet Appmenu** and [**here** is shown how it can be added to the panel]("http://askubuntu.com/questions/4681/how-do-i-enable-a-mac-style-global-application-menu-in-classic-desktop-edition")

Actually have the **Indicator Applet Appmenu** myself on my yesterday installed new 10.10 Ubuntu install. No complaints so far...

Good luck!

Wiebeest

---

### Post by ankspo71 on 2010-10-11
> **wiebeest said:**
> 
The netbook remix version is called **Indicator Applet Appmenu** and [**here** is shown how it can be added to the panel]("http://askubuntu.com/questions/4681/how-do-i-enable-a-mac-style-global-application-menu-in-classic-desktop-edition")


Thanks for that info. I tried searching for it in the 10.10 repos yesterday, but I couldn't find it... so I assumed it couldn't be installed separately. I can see indicator-applet-appmenu in the repos now though, so I probably miss-spelled the keywords I used.

---

### Post by trentscott on 2010-10-11
> **wiebeest said:**
> There allready was global menu, available from here:[**global menu -link**]("http://code.google.com/p/gnome2-globalmenu/")

The netbook remix version is called **Indicator Applet Appmenu** and [**here** is shown how it can be added to the panel]("http://askubuntu.com/questions/4681/how-do-i-enable-a-mac-style-global-application-menu-in-classic-desktop-edition")

Actually have the **Indicator Applet Appmenu** myself on my yesterday installed new 10.10 Ubuntu install. No complaints so far...

Good luck!

Wiebeest

I knew of Global Menu but there aren't currently any repos for 10.10 yet. Indicator Applet Appmenu is different than Global menu. I'm looking for the launcher icons at the bottom of the screen like a mac, not necessarily the file, edit, etc.. menus at top. Has anyone come across how that can be done on 10.10?

---

### Post by alokmenon on 2010-10-11
Do you mean a launcher applet/dock like [AWN]("http://wiki.awn-project.org/") or [Docky]("http://do.davebsd.com/wiki/Docky") ?

---

### Post by trentscott on 2010-10-11
> **alokmenon said:**
> Do you mean a launcher applet/dock like [AWN]("http://wiki.awn-project.org/") or [Docky]("http://do.davebsd.com/wiki/Docky") ?

That's what I was looking for! Thank you. Any preference between the two? At first glance Docky looks better....

---

### Post by FiveSidedPoly on 2010-10-11
Through tests that I have done, AWN uses a lot less resources then Docky, not sure if it matters to you or not.  But just sharing that info.
 
Also you can run AWN with Compiz turned off and still get the great effects by using Metacity with compositing turned on.  Also saving running resources.

---

### Post by glitch323 on 2010-10-11
They're both great, but I think I like AWN just a little bit better.  It seems to have more ways to customize it, and windows can go underneath it when you maximize them (has to be set to 'always on top').  I don't like the way it looks when you maximize a window and it stops at the top of the dock bar.  I haven't found a way to fix that with Docky.

---

### Post by simonmoon42 on 2010-10-11
Yeah. I tried both Docky and AWN and AWN won out. I just liked the options better.

---

### Post by redseventyseven on 2010-10-29
> **glitch323 said:**
> They're both great, but I think I like AWN just a little bit better.  It seems to have more ways to customize it, and windows can go underneath it when you maximize them (has to be set to 'always on top').  I don't like the way it looks when you maximize a window and it stops at the top of the dock bar.  I haven't found a way to fix that with Docky.

It can be done in Docky as well.

Clicking the anchor icon on the left hand sind of the bar brings up the preferences. The option you're looking for here is "Hiding".

Admittedly there's no option for keeping the dock visible with windows maximised but the "Intellihide" setting is probably closest to what you're looking for.

---

