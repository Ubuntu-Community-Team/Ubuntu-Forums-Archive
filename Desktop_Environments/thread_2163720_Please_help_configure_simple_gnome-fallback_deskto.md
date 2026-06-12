---
title: "Please help configure simple gnome-fallback desktop"
date: 2013-07-19
forum: Desktop Environments
---

### Post by r_avital on 2013-07-19
Apologies in advance if I mix up some of the terms used in this question, I'll be as detailed as I can.

Using Raring 13.04 64 Bit.

What I would like, is to use gnome with a top panel for launchers, notifications, and indicators, a bottom panel showing running applications.  Also, I would like to use some of the features of compiz (which seems to be still buggin in 13.04 -- separte story).

To that end, I've installed the gnome-fallback package.  Upon login, I get the options for Fallback and Fallback-no effects.  I use the no-effects session to set up launchers on the top panel, and the gnome fallback -- with effects -- for actual work.  At least, that was the plan.  

Now, in a regular Gnome3 session, I get the launcher that looks like a large panel/bar on the left, what is that called, unity?  In any case, I do apologize deeply to the developers for being such a primitive boob, but I simply don't like it.  I see no progress, no advantage, in having to bump a window's titlebar against the top panel and hover over it to see the application's menu, but then again, I'm a primitive boob, so I apologize to the developers.  That's why I went through the trouble of installing the fallback session options.

So this was working for a few hours, then after enabling static application switching in compiz, I get the launch-bar on the left, IN THE FALLBACK session.  Also, I have no menus in open applications -- I mean the "File Edit View" etc menus you get with practically every application.  I found some "ask ubuntu" advice to do the following in a terminal:

dconf reset -f /org/compiz
unity --reset-icons &disown

That left me with windows with menus as I wanted, but no window titlebar. I double-checked in CCSM, the Windows Decorations was enabled.  Disabled-reenabled, same result

Rebooting into the same fallback session, I get the launcher on the left again, and no menus on any open application, which all have their titlebars.

So what I would like:

1. No big fat launcher on the left, right, or anywhere.  I want the launchers I set up on the top panel.
2. Windows should have titlebars, with the menu, min/max/close buttons.
3. Application windows should have their menus.
4. Be able to use all that in a gnome-fallback WITH effects session.

Am I expecting too much?

I'd be grateful for any assistance you can offer.  Please help, because after trying Precise-LTS-gnome with/without fallback, Precise-LTS-xubuntu, and Raring-gnome, each with its own problems, I'm at the end of my rope with Ubuntu.

Thanks in advance, and again, my apologies to the developers.

---

### Post by dino99 on 2013-07-19
when you first login, you have to choose which DE you want to log with : ubuntu (aka unity) , gnome (aka gnome-shell), gnome-classic (with the buggy compiz) & gnome-classic without effects. This can be done via the gear on top right corner of lightdm login screen.

The stock 13.04 is still using the old fashioned gnome2 (3.6) look & feel which you get when you are logged as gnome-classic (fallback); otherwise you get the unity DE with its left vertical icons bar. You also can get the newer (and stable) gnome3 (3.8) via gnome3-team ppa
Then you can install gnome-tweak-tool and/or unity-tweak-tool and/or dconf-editor to set your favorite DE as you wish

---

### Post by r_avital on 2013-07-19
dino99,

I know you're knowedgeable about this, so thanks for the prompt reply.

I've read your reply, logged off so I could write down the options I get, and logged back in.  What I have:

Gnome Fallback
Gnome Fallback (No Effects)
System Default
Ubuntu

In that order. [System default gives me nothing more than the wallpaper, working mouse pointer, nothing else.  Clicking, right-clicking, waiting, nothing happens.  Ctrl+Alt+Del, thankfully, gives me a logout choice.  Let's leave that for another day, I can live without it]

So Ubuntu is Unity, and I know what the other two are.  Am I correct that the Gnome3 3.8 won't resolve my issue in Gnome Fallback?

I've run dconf-editor, found an entry in org/gnome/desktop/session called session-name.  It was set to ubuntu, known values are gnome and gnome-fallback.  I set it to gnome-fallback, and logged off, logged back on to gnome fallback with effects, the launcher is still there.

Bottom line: Why am I getting the launch-bar in a Gnome Fallback  (**with** effects) session?  Is that by design?  More importantly, how do I get rid of it and get my launchers on  the top panel again?

Thanks in advance.

EDIT: I've ran ubuntu-tweak and gnome-tweak-tool, neither of them lets me get rid of the launcher.  Am I missing something?

---

### Post by buzzingrobot on 2013-07-19
Have you considered MATE on Ubuntu?

---

### Post by Frogs Hair on 2013-07-19
> Bottom line: Why am I getting the launch-bar in a Gnome Fallback (with effects) session? It reads like the Unity plug-in is enabled in Classic with effects and shouldn't be . If you have the Compiz Configuration Settings Manager installed the Unity plug-in can be disabled in Classic w/effects. I can't answer why Unity is enabled in that session other than it may be a bug or glitch. I have classic installed as a result installing the Gnome Shell, but prefer the XFCE session over  Classic.
 
There is a good guide for Classic no effects if you are interested interested and as written above Mate is a Gnome 2 fork which is like the old desktop.
   
[http://www.webupd8.org/2013/04/mate-16-released-install-it-in-ubuntu.html](http://www.webupd8.org/2013/04/mate-16-released-install-it-in-ubuntu.html)

---

### Post by r_avital on 2013-07-19
Thank you buzzingrobot and Frogs Hairs,

I had uninstalled the Compiz Unity plugin altogether, and all app windows showed up with no window titlebar.  I re-installed it, and somehow it got re-installed in an enabled status.  Disabling it took the launcher away, but hovering over the top panel with an open application on desktop did NOT show me the app's menu.

And Yes, I had just heard of MATE for the first time afer my previous post, and been experimenting with it.  Looks like a viable solution.

I don't want to bother the wrong members by posting in the wrong forum.  MATE is a Mint product, so I'm wondering -- where should I post questions on issues with MATE under Ubuntu Raring, so it is not moved?  Or should I try a different forum altogether?

For instance, right now, in a MATE session in Raring:

1. I have three icons on the desktop ("Computer" "so and so's Home" and "Trash") that I can't get rid of, even though the gnome-tweak-tools configuration shows them "off" -- even under Gnome-Fallback.  In both Gnome-Fallback and Mate, the "delete" context-menu option for these is grayed-out.

2. The clock/calendar applet thatr is supposed to interface with the calendar in evolution, doesn't -- doesn't show upcoming events, doesn't launch the evolution calendar when double-clicking on a date in the applet, etc.

Where would I post questions about such issues?

Last question -- it seems many people agree that Unity is a young product still searching for direction, and that as it stands now it's a great click and time waster.  Is there a feedback area to the developers, that they would read to glean some "polite insight" as to what to do with unity?

Many thanks!

---

### Post by buzzingrobot on 2013-07-20
MATE is an independent project. 

Gnome-Tweak-Tool doesn't know about MATE.  It's a tool to manipulate Gnome 3.

I'd post MATE questions in this form or at the forums at mate-desktop.org.  This forum gets the most traffic, by far.

I'm not excited about Unity's default aesthetics, but, for usabililty, I find it just fine.  I typically keep a number of apps open in individual workspaces.  Switching between them with Unity's Launcher is a one-click affair.  I.e., clicking on the icon of an open app displays that app in its workspace. Can't do that in Gnome 2/MATE. Gnome Shell actually takes it one more step by automatically creating workspaces and deleting empty workspaces.  I.e., I can open a new app in a new work space with one click and without manually creating that new workspace.

---

### Post by Frogs Hair on 2013-07-20
There are definitely Mate/Ubuntu users here and  a new thread with Mate specific questions and a fitting title may get more attention than the current thread.  I use different window managers in order to learn my way around them, but Ubuntu is my starting point.

---

### Post by cmcanulty on 2013-07-30
try these 2 links very clear and easy also see my screenshots of my classic setup. Panels can be any side you like 
[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed]("http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed")
[http://www.ubuntugeek.com/how-to-install-classic-gnome-desktop-in-ubuntu-12-04-precise.html]("http://www.ubuntugeek.com/how-to-install-classic-gnome-desktop-in-ubuntu-12-04-precise.html")
Well we have the forums back but now screenshots won't upload sorry

---

