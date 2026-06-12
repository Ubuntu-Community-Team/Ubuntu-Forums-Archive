---
title: "XFCE Panel Items (or replacements) in Gnome - Mail Checker, Icon Box"
date: 2006-08-23
forum: Desktop Environments
---

### Post by thetictacaddict on 2006-08-23
I installed XUbuntu about 3 weeks ago and have been loving the experience.  XFCE is nice, but I wanted a change so I decided to install the ubuntu-desktop package today and try Gnome.  At first, I thought, "Wow! this seems prettier, and runs at least as fast if not faster."  But then I found myself wishing for some things from XFCE.

I really like some of the panel items in XFCE, like Mail Watcher and Icon Box for instance.  I use Mail Watcher to keep tabs on a gmail account and a pop3 account, and I prefer Icon Box to Task List, because it's less cluttered: it is a list of open running applications, identified only by an icon, not the window title.  Also, the buttons in the Icon Box don't change size every time a window is opened or closed, which is nice.

Can anyone suggest replacements for these Panel Items (or perhaps better yet. a way to use them in gnome)?

I feel like I'm asking for some really specific solutions to some small issues, but any advice or information is appreciated!

---

### Post by bmadaras on 2006-09-11
I too am interested in the applets that seem to come with the xfce panel, but I have not found anything comparable besides gdesklets which I am not a fan of since I want to keep the info on the panel.  Can someone give us a heads up on where to look for applets for the gnome panels besides the ones that come by default.

---

### Post by groggyboy on 2007-01-11
kinda old thread, but it inspired me...

i couldn't find anything like Icon Box for gnome.  instead, my solution was simply to use the XFCE panel in my gnome session.  if you don't have xubuntu installed, then you need to install the package "xfce4-panel" plus whatever xfce panel plugins you want to use (Icon Box gets installed by default).  I wanted to mix and match gnome applets and XFCE panel plugins, so I made sure "xfce4-xfapplet-plugin" was also installed.  For other plugins, just search synaptic for "xfce panel" or "xfce plugin".

Then, to test it, run "xfce4-panel" from the command line.  After setting it up the way you want it, go to System>Preferences>Sessions, and chose the "Startup Programs" tab.  Click "Add", and enter "xfce4-panel".  Save and exit.  Log out and back in again (by hitting Ctrl-Alt-Backspace), and the panel loads up.  Voila!  It will also stay across reboots now.

Some tips on customizing the XFCE panel, for those who are unfamiliar with it: to customize the panel's placement, its size, or to add or remove new panels, right click anywhere on the panel and choose "Customize Panel" (adding or removing panels is done by clicking the giant Plus and Minus signs beside the popup menu where it says "Panel 1").  To add items to the panel, right click and choose "Add New Items".  To use gnome applets, scroll down to the bottom of the window that appears, and choose "Xfapplet".  Another window appears with all your available gnome applets.

Some issues to be aware of: if you use both DE's, customizing the XFCE panel for gnome will also affect it's appearance in Xubuntu.  As well, certain plugins won't work in Ubuntu, nor will certain applets run via Xfapplet.  Most notably, "trash".  Neither the XFCE plugin nor the gnome applet will refresh to reflect the Trash's empty or full status.

Well, that was long winded, but there you go.  Have fun!

---

