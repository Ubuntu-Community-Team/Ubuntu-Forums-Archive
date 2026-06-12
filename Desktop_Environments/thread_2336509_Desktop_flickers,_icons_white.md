---
title: "Desktop flickers, icons white"
date: 2016-09-08
forum: Desktop Environments
---

### Post by watchpocket on 2016-09-08
[COLOR=#008000]*(This is an updated & more coherent re-working of a previous question.)*[/COLOR]

I have a serious problem on Ubuntu-MATE 16.04:  My desktop flickers like a strobe light (doesn't stop), and all icons  are white. (Icons also have a red "X" on them.) This happened  as a result of installing & opening the ebook reader Calibre. (Happened instantly.)

  The background image at the greeter login page is also gone.  (The username & password boxes are still there -- but background  is black -- so I can log in and issue terminal commands between  flickers. The terminal autostarts, so it's already up.  I can also access the virtual terminal.)

  Running [COLOR=#0000ff]***sudo apt install --reinstall ubuntu-mate-desktop***[/COLOR] warned of 3 unmet dependencies:

  (1) [COLOR=#0000ff]**apturl**[/COLOR] *("but it is not installable");*
  (2) [COLOR=#0000ff]**compiz-plugins**[/COLOR] *("but it is not going to be installed")*; and
  (3) [COLOR=#0000ff]**ubuntu-mate-core**[/COLOR] *("but it is not going to be installed")*.

  It also warned: [I]"Unable to correct problems, you have held broken packages."
[/I]
  I created a 2nd user, where the problem is less severe: no flickering, just white icons. [B]I'd like to start to troubleshoot from there.
[/B]
  On the 2nd-user account, the panel and menu icons are all white with  the red X. The icons on the desktop are just white, with no X.

  Graphics card is Nvidia GeForce GTS 450, driver 367.44.

  The *.xsession-errors* file for the 2nd user has several "unrecognized image file formate" warnings like this . . .

  [I][COLOR=#800000](caja:4609): Gtk-WARNING: Error loading theme icon 'image-missing' for stock: Unrecognized image file format[/COLOR]
[/I]
  . . . for several different apps. (Caja is MATE's Nautilus.)

  and like these:

  [COLOR=#800000]*sys:1: Warning: /build/glib2.0-7IOYw/glib2.0-2.48.1/./gobject/gsignal.c:2635: instance '0x7fc16c00aa70' has no handler with id '21847'*[/COLOR]

  [I][COLOR=#800000]mate-session[4217]: Gtk-WARNING: Error loading theme icon 'image-missing' for stock: Unrecognized image file format[/COLOR]
[/I]
  [I][COLOR=#800000]Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.[/COLOR]
[/I]
  [I][COLOR=#800000]Window manager warning: Got a request to focus the nofocus_window with a timestamp of 0. This shouldn't happen![/COLOR]
[/I]
  [COLOR=#800000][I]mate-screensaver: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.
[/I][/COLOR][URL="http://pastebin.ubuntu.com/23152671/"]**The full .xsession-errors file is here.**
[/URL]
(It was suggested [here]("https://ubuntuforums.org/showthread.php?t=821450")  (in 2009, at the bottom of the thread) that removing the *.local* dir  from the home dir would solve the icons problem. So I did that for the 2nd user but it had no effect.)[COLOR=#800000]

[/COLOR][COLOR=#000000](It was also suggested on a non-ubuntu forum that reinstalling librsvg would solve the problem.  I didn't do that because, at least on MATE, librsvg2-2 has about a hundred dependencies.) 
[/COLOR]
  [B]What I'd like to do, if possible, for starters, is restore the icons on the 2nd-user login.
  [/B](Though dealing with the dependencies problem might be a better starting-point.)

  Would anyone have suggestions of how to do that, and how I might get rid of the "unrecognized file format" warnings? Thanks.

---

### Post by watchpocket on 2016-09-12
This issue was solved today with a simple upgrade using the Software  Updater.  I think a new version of the MATE desktop was updated, and I  think this was as a result of my having added a key ubuntu-mate  repository that I did not previoulsy have in my software sources.

---

