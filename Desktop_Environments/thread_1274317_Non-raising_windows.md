---
title: "Non-raising windows?"
date: 2009-09-24
forum: Desktop Environments
---

### Post by 1clue on 2009-09-24
Hi,

I just got a new box, installed Ubuntu on it.

My old box (also Ubuntu, 9.0.4) I have it set up such that when you click in the window border the window raises, *but if you click in the content it does not.*  Focus is on mouse-over but focus does not raise the window.

So for example, I'm running Eclipse.  I try to debug my app, and the window pops up for the app I'm debugging.  I can click on the Eclipse debugging buttons, or type in the source code, and the app I'm working on stays on top.

The new box, this doesn't work -- There is no setting for it.  I'm lost as to what is missing.  I can sort-of get the same behavior by telling the app window to always be on top, but then when I open one of the sub-windows of the app, that window is under my main one.  This is not good either.

Anyone know right off the bat what I need to do to get this setting back?

Thanks.

---

### Post by Giblet5 on 2009-09-24
Are you running the Metacity window manager (Gnome) or KDE?

This will be a window manager property but you'll have to research *which* property. 

"raise-on-decoration-click" is not a behavior I've used.

---

### Post by 1clue on 2009-09-24
Gnome, it's stock Ubuntu.

---

### Post by Giblet5 on 2009-09-24
A quick search indicates that the sawfish WM can be configured to behave that way. I don't see a way to make metacity (gome WM) do this. I didn't try very hard.

Did that behavior exhibit ONLY in Eclipse? (Casts wary eye at JRE updates)

Here's a discussion about sawfish [focus/raise behavior]("http://forums.fedoraforum.org/archive/index.php/t-11479.html").

You'll have to dig to find out whether Metacity can do this.

---

### Post by 1clue on 2009-09-24
No, it behaved that way across the board.  I don't think I fiddled with window managers much on the last box, I just clicked something and got it that way.

I used Sawfish once, but that was back a year or two and not on Ubuntu. Either Gentoo or maybe Suse or Slackware.  Or I had a Debian box too.  My reason for using Ubuntu is so I can just run stuff without too much messing around.

<soapbox>
In spite of what happened in the early days of Java, it is really pretty consistent now across host architectures.  The one exception I know of is Mac OS, where the UI changes they made are nonstandard.  That can be a bit of a pain, but in this case I'm talking about, the host window manager handles the focus and raising of windows, not Java.  In that way, any "inconsistency" would be between different operating systems and their configured window focus practices.  In other words, they're consistent with the OS rather than the JVM on some other OS.
</soapbox>

Thanks.

---

### Post by psic on 2009-11-28
Seems someone else is looking for the same thing I am - 'no raise on click'.

Where could I try to find this setting for Metacity?

---

### Post by yossell on 2009-11-28
@psic - try looking at the config editor for metacity.
alt+f2, type
gconf-editor

then choose apps, metacity and under general, there are some choices about how positioning your mouse affects focus, and whether it raises the window. By a little mucking around, I can make a window active without raising it to the top by positioning my mouse over a window, but not clicking it, allowing me to type into it while another window is top. Perhaps you can get a way of getting what you want round about here.

@1clue, I'm on 9.04, and, at least for me, a lot of this kind of behaviour does seem to depend upon whether I'm running compiz or metacity. If you're running metacity, then perhaps my suggestion for @psic will help. If you're running compiz, then it may be best to bring up the configuration manager, (alt+f2, type ccsm) and play around with the plugins. Anything metacity can do, compiz seems to be able to do too. 

Normally, you can tell what's running by checking whether you're running with system-appearances-preferences and the tab visual effects. If it's set to none, then it's metacity; if one of the other values, then it's compiz - I believe.

yossell

  In metacity

---

### Post by psic on 2009-11-28
@yossell:

A big thanks for that, there's an option right where you wrote to look for it :)

Too bad this isn't in the menu under 'windows', not sure why not.

---

