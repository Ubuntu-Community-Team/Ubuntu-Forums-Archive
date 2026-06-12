---
title: "Lucid: Black screen at start up, no gnome panel"
date: 2010-09-03
forum: Desktop Environments
---

### Post by TheJimtasticOne on 2010-09-03
Hello! I'm using Mint (have posted this at [http://forums.linuxmint.com/viewtopic.php?f=55&t=54540&p=312390#p312390](http://forums.linuxmint.com/viewtopic.php?f=55&t=54540&p=312390#p312390)), but I think this might be related to ubuntu so I'm posting here as well. It's a nasty problem, I have no idea what's causing it.

For the first few starts, everything worked awesomely. Now though, when I turn on the computer, after the splash screen I get a black screen with my mouse pointer (which I can move) and nothing else. I restart X (Ctrl+Alt+Backspace), and get my login screen. Then I log in, and I get the background of the login screen and nothing else. From what I can gather, neither nautilus nor gnome-panel start up, so I don't get the panel or any icons or even my desktop background.

I can start a terminal with Ctrl+F12 (a shortcut I defined with Compiz, so that's evidently working) and start gnome-panel there (and nautilus if I want). But the theme is all wrong! Also, I can't log out or power off from the menu (Quit, Lock Screen and Log out all don't work). What's happening?!

I've done a bit of googling, there are some people who got a similar problem a few months ago (March it started), but that was to do with mangled *.desktop files in /usr/share/applications - I've checked them, they're all fine. I can't think what it might be. Can anyone help please? :)

P.S. Same thing happens in low graphics mode.
P.P.S. Very odd thing: when the screen is black except for the mouse, I can press return, enter my password and log in as normal, although the screen stays black. Then I can open a terminal and start the panel as described.

---

### Post by TheJimtasticOne on 2010-09-03
The plot thickens. I tried using recovery mode boot and selecting the option for dpkg to repair broken packages; after a while (looks like it installed a new kernel) it finished, but the symptoms are the same.

What's weird is that nautilus and all my programs weren't displaying correctly (As in wrong theme, wrong icons), so I went to appearance and reselected the theme - everything back to normal immediately, except nautilus until I restarted it... Anyone have any clues for me? :)

Oh, and compiz keyboard shortcuts seem to work, but none of the effects do.

---

