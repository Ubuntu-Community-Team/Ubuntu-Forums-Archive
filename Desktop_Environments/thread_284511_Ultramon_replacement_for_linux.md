---
title: "Ultramon replacement for linux?"
date: 2006-10-25
forum: Desktop Environments
---

### Post by srafx on 2006-10-25
I just recently switched to linux...and found replacements for about 95% of all my applications I use, but one that I cant find a replacement for is ultramon.  

Ulramon allowed me to rightclick a window and send it to another monitor, show tasklist of only windows in that monitor (not all on both monitors) and some other need features like that.

link: [http://www.realtimesoft.com/ultramon/](http://www.realtimesoft.com/ultramon/)

Is there anything like this for linux?  Also, all dialogs pop up in the middle of both monitors, is there anyway around that?...or maybe a app that helps handle windows better for dual monitors?

---

### Post by jzlharvey on 2007-02-05
Id be interested in this same app. I recently made the switch... I am looking for something to thow the taksbar over to the other monitors

---

### Post by jzlharvey on 2007-02-05
I found a solution!

Just add a a panel to each monitor you want, and add to that panel a window list. That’s it.

Instructions:
1.) Right click on anywhere on the launchbar, click “New Panel”
2.) Drag that to any monitor.
3.) Right click on that panel, and click “Add to Panel”
4.) Select “Window List” under Desktop and Windows
5.) Click Add.
6.) Click Close, and you’re done.

---

### Post by hungrybuddha on 2007-02-09
> **jzlharvey said:**
> I found a solution!

Just add a a panel to each monitor you want, and add to that panel a window list. That’s it.

Instructions:
1.) Right click on anywhere on the launchbar, click “New Panel”
2.) Drag that to any monitor.
3.) Right click on that panel, and click “Add to Panel”
4.) Select “Window List” under Desktop and Windows
5.) Click Add.
6.) Click Close, and you’re done.

I think the feature we're really looking for are the buttons on the titlebar... one that maximizes to the size of the entire desktop, and another that takes the active window and places on the other monitor. Those two buttons and their convenience are what makes ultramon so useful.

---

### Post by jdmwood on 2008-03-13
Check out this:

[http://evaost4.free.fr/swapmonitor-1.0.tar.bz2](http://evaost4.free.fr/swapmonitor-1.0.tar.bz2)

It is an app a friend of mine wrote which "flips" which screen the currently active window is on.

If you assign this to a keyboard shortcut then this covers another bit of functionality of Ultramon.

---

### Post by benlen on 2008-06-08
> **jdmwood said:**
> Check out this:

[http://evaost4.free.fr/swapmonitor-1.0.tar.bz2](http://evaost4.free.fr/swapmonitor-1.0.tar.bz2)

It is an app a friend of mine wrote which "flips" which screen the currently active window is on.

If you assign this to a keyboard shortcut then this covers another bit of functionality of Ultramon.

This was what I was looking for!
However it did not  work on my system it only sent from left to right and not right left. This is probably because of differences in how the screens are set up.

I modified the app a bit to make it work for me:
[http://bendik.lenaes.com/diverse/swapmonitor-1.1.tar.bz2]("http://bendik.lenaes.com/diverse/swapmonitor-1.1.tar.bz2")

For the keyboard shortcut (I use Ctrl +|) I used this method B as described here:
[http://ubuntuforums.org/showthread.php?t=79560]("http://ubuntuforums.org/showthread.php?t=79560")

xev told me that I should use <Control>bar for my Ctrl+| (pipe) shortcut.

---

