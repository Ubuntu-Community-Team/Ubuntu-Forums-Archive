---
title: "Right-click glitchy, Firefox display issues, locked panels don't stay locked"
date: 2009-01-04
forum: General Help
---

### Post by tony_clifton on 2009-01-04
I'm not sure if these are really Ubuntu problems, could be Firefox, Gnome, etc, specific, but I am starting here in the hopes of being led in the right direction at the very least.  Also, hopefully no one will hate me too much for posting multiple issues in one thread, so here goes:

**A)** _Right click issues_: Nearly half the time I attempt to use the right-click on my trusty mouse, expecting a menu to pop up, rather than getting the menu and being able to select from it, one of the options are automagically selected for me (the "I'm feeling lucky" method of handling simple tasks).  For instance I will highlight a link intending to copy the text, but upon right-clicking the highlighted area I get no menu at all, but then Evolution starts up and starts asking for all sorts of information I have no intention of giving it.   This is maddening.  Happens in Firefox a lot, I'm not sure if I've experienced it elsewhere.   My girlfriend has reported the same problem when using my computer.

**2)**  _Firefox display issues_:  Upon starting a new Firefox window it opens in some strange and wonderful SuperSize mode, blocking out everything else on the desktop including my wandering panels (that's next) which it should not ever block, and ranging so wide the top menus are not visible.   Hitting F11 twice fixes the issue, however it still occurs with every new instance of opening the program.  Likewise, maddening.

**d)**  _Locked panels wander where they may_:  I have kept the two panels that come with the default install, customizing them a bit.  Also I have them both at the bottom of the screen, stacked.  Additionally, for each panel I have selected "lock panel position" and this works fine for each session, however after a reboot usually they will be out of order (still on the bottom of the screen but their order is reversed).   At this point I have to move them back into position and lock them again.   Also maddening.

**Four)**  _Tops of windows sometime flicker on mouse-over_:  The tops of each window should be the brown title bar with the min, max, and close buttons.  However often when mousing over the buttons area and/or when maximizing the window, the bar will go to a blank gray with no buttons visible.  This happens with all windows, all programs.   Strange but true.

Well, there we have it.  Thanks in advance for any tips, advice, comments, rants, etc.

Cheers

---

### Post by tony_clifton on 2009-01-04
2 and Four I may have "fixed" by going to System->Preferences->Appearance->Visual Effects and selecting "None".

---

### Post by 81wtbvi02 on 2009-01-16
I've definitely got the same problem with the title bar that occasionally blanks out on mouse-over, and the self-unlocking rearranging panels.  I haven't noticed the others you mention, but I only use Ubuntu occasionally.

Here's the output from 'uname -a': ```
Linux box_name 2.6.27-10-generic #1 SMP Fri Nov 21 19:19:18 UTC 2008 x86_64 GNU/Linux
```  I have Gnome Panel 2.24.1 installed, and I think I've got Ubuntu 8.10 installed, but I can't prove it, because the version number is missing from the "About Ubuntu" screen!

I have attached a screen shot that demonstrates the title bar problem, and also shows that the version and release info is missing from the "About Ubuntu" screen.
[ATTACH]100038[/ATTACH]

---

### Post by ricardisimo on 2009-04-02
> **tony_clifton said:**
> **A)** _Right click issues_: Nearly half the time I attempt to use the right-click on my trusty mouse, expecting a menu to pop up, rather than getting the menu and being able to select from it, one of the options are automagically selected for me (the "I'm feeling lucky" method of handling simple tasks).  For instance I will highlight a link intending to copy the text, but upon right-clicking the highlighted area I get no menu at all, but then Evolution starts up and starts asking for all sorts of information I have no intention of giving it.   This is maddening.  Happens in Firefox a lot, I'm not sure if I've experienced it elsewhere.   My girlfriend has reported the same problem when using my computer.

Maddening is right. Mostly it's either Evolution wanting to send whatever I have highlighted as a link via email, or also DownThemAll! saving lord-knows-what lord-knows-where while I am just trying to copy and paste plain text to gedit.

My assumption up until now has been that I have too many plugins and add-ons in FF, and that I've overloaded the poor browser. Then I got a whiff of what other people do with their Firefox, and I'm a featherweight by comparison. My comp is hardly state-of-the-art, but it's not a Commodore 64 either.

Any ideas what's going on? I'm going to check Launchpad right now to see if we're the only ones.

---

### Post by ricardisimo on 2009-04-02
Ta-dah!

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/187313](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/187313)

It claims that a bug fix has been released, but I'm not seeing it. There was a FF update just about a week ago, but I've still got the same problem. You?

---

### Post by kanikilu on 2009-04-02
> **ricardisimo said:**
> I'm going to check Launchpad right now to see if we're the only ones. You're not. The "glitchy" context menu in Firefox on 8.10 is a pretty commonly reported problem, and I believe there is a bug open for it.

Here's a longer thread on it with links to the bug report and other similar threads:

[http://ubuntuforums.org/showthread.php?t=1011962](http://ubuntuforums.org/showthread.php?t=1011962)

// Edit - nevermind, you found it.

---

### Post by kanikilu on 2009-04-02
> **tony_clifton said:**
> **2)**  _Firefox display issues_:  Upon starting a new Firefox window it opens in some strange and wonderful SuperSize mode, blocking out everything else on the desktop including my wandering panels (that's next) which it should not ever block, and ranging so wide the top menus are not visible.   Hitting F11 twice fixes the issue, however it still occurs with every new instance of opening the program.  Likewise, maddening Check out this thread:

[http://ubuntuforums.org/showthread.php?t=993013](http://ubuntuforums.org/showthread.php?t=993013)

---

