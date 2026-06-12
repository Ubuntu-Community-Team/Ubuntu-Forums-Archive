---
title: "How to tame the Gnome menu?"
date: 2018-07-28
forum: Desktop Environments
---

### Post by frankvw on 2018-07-28
I've been using Gnome 2 on Ubuntu 12.04 for years, and now that have switched to 18.04 (clean install after previous laptop died) I've resorted to the [Frippery Gnome extensions]("https://frippery.org/extensions/") to give me a traditional menu (among other things). Unfortunately the limitations in menu management that existed in Gnome 2 years ago appear to have persisted, and right now it's a right royal mess.

I started using 'alacarte' (or "Main  Menu" in the menu) but my problem was that a lot of applications were in a very strange (and, to me, wrong) category. The settings for Adobe Flash Player are located in 'Sundry' while the 'Disc Image Mounter' lives in 'Other' but the 'About' option is located in 'System Settings' and the 'Characters' option in 'System Tools" brings up something called "Smileys and People". None of that makes sense to me.

Because alacarte won't let me move menu entries from one category to another, I then tried 'menulibre' (appearing as  "Menu Editor" in the menu) which will let me do that, But now many options (both categories and menu entries associated with applications) appear multiple times. 'Accessories', 'System Tools', 'System Settings' and "Sound & Video" all appearing twice, and the Amarok music player appears under 'Accessories', 'Other' AND under 'Sound & Video' where it appears twice! The SQLite3 browser appears in both 'accessories' and 'programming', and 'files' is all over the place.

Worse, if I make an application invisible by unchecking the 'Show' checkbox in alacarte, it disappears in all categories, and if I delete it, I delete it from all categories!

Part of the problem MAY be that some of the *.desktop files live in /usr/share/applications while others sit in ~/.local/share/applications. However, the latter I need because the Frippery Panel Favourites relies on them to put my own favourites in the top bar.

So. How can I clean up this mess? Both alacarte en menulibre only make it worse.

Also, is there any hope of this menu (which, with the introduction of Unity several years ago, seems to have fallen by the wayside somewhat) being improved and made more manageable in the foreseeable future?

All suggestions would be appreciated!

---

### Post by #&amp;thj^% on 2018-07-28
I love the Title to your thread. :D
This might not be all that you want but worth a consideration: [https://linuxconfig.org/how-to-add-start-menu-to-gnome-ubuntu-18-04-bionic-beaver-desktop](https://linuxconfig.org/how-to-add-start-menu-to-gnome-ubuntu-18-04-bionic-beaver-desktop)
And this makes me love XFCE even more. ;)

---

### Post by Dennis N on 2018-07-28
If you liked the old 'Applications Places System' menu on Gnome, look into Ubuntu MATE which still has this same arrangement available (called 'Menu Bar'). Ubuntu 18.04 application launching is really focused on the dock for launching favorites and showing/switching running applications, and the Activities Overview screen - the search works well to start applications from a couple of letters in the name. Also can display a grid of icons of favorite (or all) applications there. After a while, you get used to it - now I prefer it to menu.

That said, I installed the "applications menu' by fmuellner extension to get a category view when I want it, but I find I rarely use the menu anymore.

---

### Post by frankvw on 2018-07-30
> **1fallen said:**
> I love the Title to your thread. :D
This might not be all that you want but worth a consideration: [https://linuxconfig.org/how-to-add-start-menu-to-gnome-ubuntu-18-04-bionic-beaver-desktop](https://linuxconfig.org/how-to-add-start-menu-to-gnome-ubuntu-18-04-bionic-beaver-desktop)
And this makes me love XFCE even more. ;)

This is an option to add a menu to the Bionic desktop. I already have that as part of the Frippery extensions. What I need is to **manage** the darn thing. Which was a pain in 12.04 and still is. :)

---

### Post by frankvw on 2018-07-30
> **Dennis N said:**
> If you liked the old 'Applications Places System' menu on Gnome, look into Ubuntu MATE which still has this same arrangement available (called 'Menu Bar'). Ubuntu 18.04 application launching is really focused on the dock for launching favorites and showing/switching running applications, and the Activities Overview screen - the search works well to start applications from a couple of letters in the name. Also can display a grid of icons of favorite (or all) applications there. After a while, you get used to it - now I prefer it to menu.
I tried gnome-flashback and Mate. While they do offer an alternative that IMO should not be necessary (a soap box I have already stood on [here]("https://ubuntuforums.org/showthread.php?t=2397182")) they still use the same underlying Gnome menu structure and handling. Which was terrible in 12.04 and still is. So switching to another desktop that uses the same Gnome menu still leaves me with the same problem.

---

