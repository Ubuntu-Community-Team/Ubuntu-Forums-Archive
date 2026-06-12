---
title: "no focus after closing application window"
date: 2013-05-30
forum: Desktop Environments
---

### Post by gleedadswell on 2013-05-30
First I'd just like to say that the more I work with it the more I like Unity.  I didn't think I would at first and the transition from gnome to unity was a bit painful, but I think in the end it has really improved my ability to manage large numbers of windows simultaneously.

I'm just noticing one thing that is now tripping me up.  When you close a window (either by clicking on the upper left corner or by using alt-f4) if there is no other open window in your current workspace then the focus ends up "nowhere".  The top status bar still lists the name of the window you just closed and all hotkeys fail to work.  So if you are closing a window and then attempting to jump to an open window on another workspace with hotkeys you have a hiccup in your workflow.

The one "hands on keyboard" way I've found around this is that the one hotkey that still works is <super>.  So if you quickly tap <super> twice (opening and immediately closing the dash) the focus lands on the desktop and you are back to being able to use hotkeys.

This seems like it ought to be simple to fix.  I assume that when you close a window the desktop environment has some series of function calls in which it searches for an appropriate place to put the focus (it usually lands on the window that was right below the one you just closed).  This series of calls needs to be modified so that if there is no window open in the current workspace the focus goes to the desktop.  Short of digging into the code of unity, does anyone have any idea how to make this happen?

---

### Post by gleedadswell on 2013-06-05
I've just put 12.04 on another computer.  On the computer I was talking about above, because the screen is not very big, I had enabled the option for the launcher to hide when not in use.  On the second computer I am leaving the launcher visible.  The problem I reported above does not exist if the launcher is left visible.

---

### Post by stinkeye on 2013-06-06
I had the same sort of focus issues in earlier releases, launcher hidden or not. The workaround I used was to put
cairo-clock on the desktop so when the last window was closed, cairo-clock would grab focus
and I wouldn't have to click on the desktop for keyboard shortcuts to work.

---

### Post by gleedadswell on 2013-06-07
> **stinkeye said:**
> I had the same sort of focus issues in earlier releases, launcher hidden or not. The workaround I used was to put
cairo-clock on the desktop so when the last window was closed, cairo-clock would grab focus
and I wouldn't have to click on the desktop for keyboard shortcuts to work.

That seems to work, but then it looks like I'd need to have an instance of the clock on every workspace.  Is there a way to have Startup Applications make multiple instances and place them each on a different workspace?

Alternatively, I have conky running.  Is there some way conky can be made to grab the focus when there is nothing else in the workspace?

---

### Post by gleedadswell on 2013-06-07
OK, I'm figuring it out.

> [COLOR=#000000]I've just put 12.04 on another computer. On the computer I was talking about above, because the screen is not very big, I had enabled the option for the launcher to hide when not in use. On the second computer I am leaving the launcher visible. The problem I reported above does not exist if the launcher is left visible.[/COLOR]

Wrong.  Now the desktop focus fails with launcher hidden or not.  The issue was that on my new install I hadn't yet set up conky.  Once conky was running the desktop focus problem returned.  This is apparently a known bug:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/934189](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/934189)

So the simple solution to this problem is to not run conky.  I hope it gets fixed because I kind of like conky, but I can live without it to get correct desktop behaviour back.

---

### Post by stinkeye on 2013-06-07
[COLOR="#FF0000"]EDIT[/COLOR] Just found the issue still exists in Raring.
Didn't notice because I'm running cairo-clock.
None of the conky stuff fixes.
cairo-clock has a right click menu for making sticky but can take numerous tries
for the menu to show.
Can set it as sticky in the ccsm window rules plugin with...
```
class=Cairo-clock
```
[ATTACH=CONFIG]243601[/ATTACH]


**Disreguard below...tried and doesn't work.**
I run conky also which  must be why I had the problem with focus before.

Try different settings in your conkyrc for  **own_window_type**
Eg 
```
own_window_type **override**
or
own_window_type **normal**
```

Also look at the setting...
```
own_window_hints undecorated,above,sticky,**skip_taskbar**,**skip_pager**
```
Maybe deleting skip_taskbar and/or skip_pager might allow conky to get focus and fix.
Test using own_window_type **normal** because 
own_window_type **override** ignores own_window_hints.

---

### Post by stinkeye on 2013-06-24
See [**[COLOR="#B22222"]THIS[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=2156795&p=12704546&viewfull=1#post12704546") post for a fix using ccsm.

---

