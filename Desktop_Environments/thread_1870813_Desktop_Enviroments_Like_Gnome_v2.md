---
title: "Desktop Enviroments Like Gnome v2?"
date: 2011-10-27
forum: Desktop Environments
---

### Post by Spice Girls on 2011-10-27
Is there any DE that is like Gnome v2? I'm not happy with the new version or Unity. I like Gnome 2 becuase it's easily customizable and easy to find everything.

---

### Post by viperdvman on 2011-10-27
I've heard a lot of good about Xfce as of late, saying that it's as close to GNOME 2 as it gets, more so than even GNOME-fallback. I haven't played with Xfce myself, so I wouldn't know. But give it a shot :)

There are two ways to do it. One (the common way), download and install Xubuntu from scratch. Two (the easier way), if you already have Ubuntu 11.10 installed, just go into the Software Center and download **xubuntu-desktop**. That should load the full Xfce desktop. Good luck :)

---

### Post by crdlb on 2011-10-27
You should give the fallback session a try: [https://help.ubuntu.com/community/GnomeClassic](https://help.ubuntu.com/community/GnomeClassic)

---

### Post by vat with tux on 2011-11-04
You can also try for KDE .... it is really coool any also more customizable ..... 
[http://tinyurl.com/5s98vdy](http://tinyurl.com/5s98vdy)

---

### Post by Rodney9 on 2011-11-04
Lubuntu is very good,

---

### Post by davdo2004 on 2011-11-04
> **Spice Girls said:**
> Is there any DE that is like Gnome v2? I'm not happy with the new version or Unity. I like Gnome 2 becuase it's easily customizable and easy to find everything.

Install  gnome-session-fallback and have a browse through some of the articles on 
[http://www.omgubuntu.co.uk/](http://www.omgubuntu.co.uk/)
[http://www.webupd8.org/](http://www.webupd8.org/)
and this one in particular  [http://www.webupd8.org/2011/11/indicator-applet-ported-to-gnome-3-can.html](http://www.webupd8.org/2011/11/indicator-applet-ported-to-gnome-3-can.html)

---

### Post by sanderd17 on 2011-11-04
Mate is a gnome 2 fork.

But you could just stay with Gnome 3. As the above post shows, most Gnome 2 things have been ported to Gnome 3 and are available in the fallback mode.

But I do prefer Gnome Shell. If you disable the overview and use a menu and a task bar instead, you get a pretty standard Gnome 2 experience.

---

### Post by gradinaruvasile on 2011-11-04
> **sanderd17 said:**
>  If you disable the overview and use a menu and a task bar instead, you get a pretty standard Gnome 2 experience.

Pretty standard. Until when? And how pretty?

Just use xfce. It is really good (im using it for quite a while and its noticeably faster than gnome even in relatively recent computers (Athlon II x2 @3.0 GHz).
You dont get all the gnome thrash runnign in the background (well if you really use xfce, xubuntu is heavier than the standard xfce) but you have most of the functionality.

---

### Post by 3Miro on 2011-11-04
If you don't like Unity or Gnome-shell, then your options are:

- gnome-fallback, which is a GTK3 port of gnome-panel and Metacity. It will be sported for now, although it may be dropped in the future.

- xfce4, very Gnome-like and actually faster than gnome, it just takes a bit more effort to setup. If you already have Ubuntu with Unity, you should just install the xfce4 package, there is no need to pull the entire xubuntu-desktop.

- KDE, the most customizable DE available at the moment, somewhat heavy though.

- LXDE, lightning fast, however, it is still work in progress and it is sometimes not that stable.

- go back to Ubuntu 10.04 (for 2 more years of support) or go for Debian 6 (at least 3 more years of support).

---

### Post by Frogs Hair on 2011-11-04
You could try Mint also  , but if you want Ubuntu 3Miro has covered the options .[http://www.linuxmint.com/rel_katya_whatsnew.php](http://www.linuxmint.com/rel_katya_whatsnew.php)

---

### Post by sanderd17 on 2011-11-04
> **gradinaruvasile said:**
> Until when? 

Until they stop maintaining gnome shell. 
> and how pretty?
8



BTW,there are no plans to drop the fallback mode, the gnome team wants to maintain it as a,separate,full DE.
And mint is just gnome shell with some extensions installed to make it look and act like gnome 2.

---

### Post by W.McL on 2011-11-04
The Gnome 3 fallback mode is buggy and not really ready to use. A few example of the small, but very annoying annoyances:
[LIST]
[*]The indicator applets for the panel haven't even been ported yet, so they won't work (some of them try very hard to pretend they work, though).
[*]The default ubuntu themes have a bug which causes the workspace switcher to fail to highlight the currently selected workspace. (for a fix see my bug report here:  [https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/881180](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/881180))
[*]The "System" menu is gone and has been replaced with gnome-control-center, so reaching simple configuration tasks will cost you at least one additional click.
[*]The "User" menu for gnome-panel is **[SIZE="4"]HUGE[/SIZE]** and effectively prevents you from making the panel it resides in smaller than 30 pixels.
[/LIST]

[EDIT]
Some hero ported the indicator applet to Gnome 3 and put it in a PPA, so some annoyances of the Gnome 3 fallback sessions are gone. :)
[http://www.webupd8.org/2011/11/indicator-applet-ported-to-gnome-3-can.html](http://www.webupd8.org/2011/11/indicator-applet-ported-to-gnome-3-can.html)
With the indicator applet back, you can remove the **[SIZE="4"]HUGE[/SIZE]** "User" menu, and all indicators work almost like you are used from Gnome 2.
[/EDIT]

Xfce is nice and fast, but usability wise it's missing a lot, it feels like an old Gnome 2 from 4 years ago.

To make it short, the latest ubuntu release with a desktop environment comparable to Gnome 2 is 11.04 with Gnome 2.

When I last tried Mint about 5 months ago, I couldn't use it because it doesn't have a textmode installer and it's GUI installer can't install on an LVM.

---

### Post by sanderd17 on 2011-11-04
> **W.McL said:**
> The Gnome 3 fallback mode is buggy and not really ready to use. A few example of the small, but very annoying annoyances:
[LIST]
[*]The indicator applets for the panel haven't even been ported yet, so they won't work (some of them try very hard to pretend they work, though).

Then what's this article about? [http://www.webupd8.org/2011/11/indicator-applet-ported-to-gnome-3-can.html](http://www.webupd8.org/2011/11/indicator-applet-ported-to-gnome-3-can.html)
> 
[*]The default ubuntu themes have a bug which causes the workspace switcher to fail to highlight the currently selected workspace. (for a fix see my bug report here:  [https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/881180](https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/881180))

I believed we were talking about DEs, not about distros. It's possible gnome has problems with the default Ubuntu theme, but why don't you use another theme (like the default Gnome theme)?
> 
[*]The "System" menu is gone and has been replaced with gnome-control-center, so reaching simple configuration tasks will cost you at least one additional click.

I don't click anymore. I hit the super key and type what I want to search. Than I arrive immediately in the right part of the gnome-control-center.
> 
[*]The "User" menu for gnome-panel is **[SIZE="4"]HUGE[/SIZE]** and effectively prevents you from making the panel it resides in smaller than 30 pixels.
[/LIST]

Xfce is nice and fast, but usability wise it's missing a lot, it feels like an old Gnome 2 from 4 years ago.

To make it short, the latest ubuntu release with a desktop environment comparable to Gnome 2 is 11.04 with Gnome 2.

When I last tried Mint about 5 months ago, I couldn't use it because it doesn't have a textmode installer and it's GUI installer can't install on an LVM.

I do think XFCE is a very good replacement, but Gnome is good too.

---

### Post by 3Miro on 2011-11-04
> Xfce is nice and fast, but usability wise it's missing a lot, it feels like an old Gnome 2 from 4 years ago.

I don't want to start flame wars, I am just wondering about is it that you find missing in xfce4. I can think of couple of minor problems and some things that have to be manually set, but on the other hand xfwm4 has more options than Metacity. Maybe I am missing something here.

Could you list the features that you are missing?

---

### Post by W.McL on 2011-11-04
> **3Miro said:**
> I don't want to start flame wars, I am just wondering about is it that you find missing in xfce4. I can think of couple of minor problems and some things that have to be manually set, but on the other hand xfwm4 has more options than Metacity. Maybe I am missing something here.

Could you list the features that you are missing?

It has been a few weeks since I tested Xfce out of frustration over gnome3-fallback, so I don't remember the details anymore, but it wasn't one big thing, but more like many very small problems which interfered with the way I work, and I didn't investigate them any further, because I was in a hurry getting a system I could work with.

> **sanderd17 said:**
> 
I believed we were talking about DEs, not about distros. It's possible gnome has problems with the default Ubuntu theme, but why don't you use another theme (like the default Gnome theme)?


Well, I assumed this thread was mainly about the available DEs on ubuntu, sorry if I got that wrong. The theme thing is more a personal preference, but the bug is still a bug.


> **sanderd17 said:**
> 
Then what's this article about? [http://www.webupd8.org/2011/11/indic...ome-3-can.html](http://www.webupd8.org/2011/11/indic...ome-3-can.html)


Just noticed right after I posted, see my edit...

> **sanderd17 said:**
> 
I don't click anymore. I hit the super key and type what I want to search. Than I arrive immediately in the right part of the gnome-control-center.


Sometimes I search too, but sometimes I prefer to click (like when I just have the hand on the mouse, so I don't have to move over to the keyboard) and I don't like any DE to shove a certain way of usage down my throat by making other ways undesirable on purpose.

---

### Post by Simian Man on 2011-11-04
Just use KDE.

---

### Post by 3Miro on 2011-11-04
> **W.McL said:**
> It has been a few weeks since I tested Xfce out of frustration over gnome3-fallback, so I don't remember the details anymore, but it wasn't one big thing, but more like many very small problems which interfered with the way I work, and I didn't investigate them any further, because I was in a hurry getting a system I could work with.


That's how I started, then I moved completely over and I even find Gnome 2 inferior to xfce right now (mostly becuase xfwm has more options). It will take you some time to figure out xfce and how to set things up the way you want them, and you will never have an exact clone of Gnome, but I think it is totally worth it.

---

