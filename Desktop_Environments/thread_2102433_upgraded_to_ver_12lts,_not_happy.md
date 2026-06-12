---
title: "upgraded to ver 12lts, not happy"
date: 2013-01-07
forum: Desktop Environments
---

### Post by DaveMcC on 2013-01-07
Due to various reasons, I upgraded from ubuntu 10, to ubuntu 12, there seems to be a hell of a lot missing
Starting with the top panel:_** Applications, Places, System**_; can they be restored to look like ver 10

From **System**, I have no** Preferences/ main menu / screen saver** etc
From **System**, I have no** Administration**, **Gparted Patition Editor / Synaptic Package Manager**

I have parts down that stupid child drawn thing on the lhs, but there is no screen saver, etc, (who the hell came up with THAT:? bill gates first attempt at win8?)

On the screen when you right click, **Change Desktop Background**, in the** Appearance** **Preferences / Theme**, no _Clearlooks _option?,* in fact* the** Theme** is blank

Can ver 12 be made look like version 10 ? ):P

Dave

---

### Post by 3rdalbum on 2013-01-07
Ubuntu uses the Gnome desktop environment. In between 10.04 and 12.04 the Gnome project released a re-written Gnome desktop (Gnome 3) that's virtually nothing like the old Gnome desktop (Gnome 2).

Ubuntu now uses Gnome 3 as its base, although it has its own Unity desktop sitting on top that is quite revolutionary in its own way and also nothing like Gnome 2.

So, to answer your question: There's nothing "missing", the Unity desktop is just a lot, lot different to the old Gnome 2 desktop that is now obsolete and not maintained.

The menus have been replaced with the Dash system; click on the Ubuntu icon on the left of the screen to start the Dash. You can search here across multiple "lenses" or click on a lens icon at the bottom of the Dash to be more specific. You can browse programs by clicking on the Applications icon in the Dash and clicking "Show All Results" or choosing some filters. Or typing. The Main Menu editor is still there but now it modifies the programs listed in the Applications lens of the Dash.

There is no screensaver in Gnome 3 and therefore not in Ubuntu. Clearlooks is no longer preinstalled - in fact, I'm not even sure that Clearlooks even works in Gnome 3, which would also explain why it's not installed on Ubuntu. Unless you have an old CRT monitor, who needs a screensaver anyway?

Synaptic Package Manager is not preinstalled on Ubuntu 12.04 but you can use Ubuntu Software Center, or install Synaptic from the repositories. Gparted was never preinstalled on Ubuntu, you can install it from the repositories.

It's possible to install "Gnome Fallback" on Ubuntu 12.04 (install the Gnome Panel package and choose Gnome Fallback at the login screen as always) but it too is based on Gnome 3 and does not add options to the control panels. In any case, Gnome Fallback is a deadend and is widely believed to be depreciated; it will probably be unmaintained in the future.

**My best recommendation** to you is to persist with Unity and try to get used to it. Like most others here, I originally resisted the switch to Unity, but once I started using it a bit I grew to love it. It's really a great desktop - a massive leap ahead of Gnome 2.

There is also a fork of Gnome 2 available, called MATE, but I have doubts about its longevity considering how few developers it has and how slow the pace of development is. I'd consider it a stop-gap fallback until you can get familiar with a better desktop such as Gnome 3 or Unity.

---

### Post by ajgreeny on 2013-01-07
> **DaveMcC said:**
> Due to various reasons, I upgraded from ubuntu 10, to ubuntu 12, there seems to be a hell of a lot missing
Starting with the top panel:_** Applications, Places, System**_; can they be restored to look like ver 10

From **System**, I have no** Preferences/ main menu / screen saver** etc
From **System**, I have no** Administration**, **Gparted Patition Editor / Synaptic Package Manager**

I have parts down that stupid child drawn thing on the lhs, but there is no screen saver, etc, (who the hell came up with THAT:? bill gates first attempt at win8?)

On the screen when you right click, **Change Desktop Background**, in the** Appearance** **Preferences / Theme**, no _Clearlooks _option?,* in fact* the** Theme** is blank

Can ver 12 be made look like version 10 ? ):P

Dave
You have now installed a version of Ubuntu that uses unity as its default desktop, and is underpinned by gnome 3 and GTK3, so looks and acts very differently from ubuntu 10.04.

Your options are probably best served by either using the classic desktop in your ubuntu 12.04 or moving to the LTS version of Xubuntu with the XFCE desktop.  Xubuntu is what many users are moving to if unity is not their choice.  You can add **xubuntu-desktop** to your current 12.04 installation very easily, just like any other package, then choose to use xfce/xubuntu at the login screen next time.

For the equivalent classic gnome desktop in 12.04 see [PreciseGnomeClassicTweaks]("https://help.ubuntu.com/community/PreciseGnomeClassicTweaks")

---

### Post by Impavidus on 2013-01-07
You can install synaptic from the software centre or the command line. It's no longer included by default. The same is true for the screen saver: modern screens don't need to be saved any more, but you can install xscreensaver from the repositories (I don't know whether it works with gnome 3).

The new desktop, unity, is a bit controversial. Some love it, some hate it. Some hate it at first and fall in love later. If you definitely hate unity, you can install xfce-desktop. You can run multiple desktop environments side by side, choosing one at login. Xfce is very configurable an can be made to look almost like gnome 2. It doesn't have unity's search function, but after all, if you know where to find what you're looking for, a search function is a bit pointless. That's just my opinion, of course, and I switched to xfce.

I recommend you try them both, use the one you like most and keep the other as a back-up.

---

### Post by grey1beard on 2013-01-12
I'm using Gnome in 12.04 lts on my laptop, and have all the facilities that I'm used to re 'Administration' and  'Preferences' as mentioned by the op.
However, I notice that #3 mentions > Your options are probably best served by either using the classic desktop in your ubuntu 12.04 or.... and it may be that this is what I have done since doing a clean install from a new live disk download a few days ago.
My wife's laptop has 12.04lts achieved by continual upgrades, and on hers those menu items are missing.
I conclude that I must change hers to 'classic', so perhaps ajgreeny could add the details of how to for the benefit of both the op and me ?

Regards
John

---

### Post by sandyd on 2013-01-12
**Moved to desktop environments**

---

### Post by aspergerian on 2013-01-12
DaveMcC,

I too miss 10.04 - better for my equipment, better for my brain. I tried Unity, fallback, and Mint - finally settled on Xubuntu and was helped to have top and bottom bars similar to 10.04. That thread is here [http://ubuntuforums.org/showthread.php?t=2098800](http://ubuntuforums.org/showthread.php?t=2098800)

---

### Post by tartalo on 2013-01-12
[http://askubuntu.com/questions/65083/what-different-desktop-environments-and-shells-are-available](http://askubuntu.com/questions/65083/what-different-desktop-environments-and-shells-are-available)

Also, if you are concerned about Long Term Support:
- Kubuntu 12.04 LTS -> 5 Years
- Xubuntu 12.04 LTS -> 3 Years

---

### Post by Bucky Ball on 2013-01-12
To try xfce, just install xfce4 from the Software Centre, log out, choose it from the Sessions pop-up. Log in.

I wouldn't advise installing xubuntu-desktop, that is different; it is basically like installing Xubuntu BUT this means it will drag in all apps, dependencies and everything else default in xubuntu. You don't want that. This means your application menus, for example, will have all of the Ubuntu default apps AND the Xubuntu ones which you don't need.

You only want the desktop environment, xfce4. Good luck.

---

