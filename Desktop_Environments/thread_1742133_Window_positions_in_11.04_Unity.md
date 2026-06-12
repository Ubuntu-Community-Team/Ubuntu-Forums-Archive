---
title: "Window positions in 11.04 Unity"
date: 2011-04-28
forum: Desktop Environments
---

### Post by ubnoobie on 2011-04-28
I have booted-up using the Ubuntu 11.04 live DVD. System is AMD 780g-based with HD5600-series graphics card added. Display is a single 1280x1024 monitor.

Open a program. Double-click title bar to maximize. Double-click the top bar (whatever it's called) to restore the window and its original position is not preserved... making matters worse is that often the window position is partially off screen (to right), and if you maximize and restore again, it's worse (further and further to the right) every time.

Screen shots attached show original window size and position, and window position after being maximized and restored once, and then a second time via double-clicking the title bar.

This does not occur if you use the maximize/restore icon instead of double-clicking the title bar.
___

Also....

I want a window of a newly opened program to be located and sized as it last was with that program... current behavior of automatically sticking windows wherever the system thinks they should go (presumably based on some routine that determines most 'open' space on workspace) is very annoying.

---

### Post by TrakerJon on 2011-05-01
I'm having a similar issue, the Unity desktop doesn't retain window positions. 
It tends to send them to the top left or open them in maximized view (Firefox specifically). 
Compiz freaks out if you try to use the desktop cube feature as well.
Did they fully test this OS before releasing it?

Dell GX270, 3.2Ghz Intel, 256Mb nVidia graphics, 2Gb SDRAM.

Traker

---

### Post by vanadium on 2011-05-01
I can reproduce this perfectly: definitely a bug.

---

### Post by bovender on 2011-05-01
+1

Many windows open in the maximized state -- they did not use to do this in Maverick -- I find it tiring having to unmaximized (and position) the application window everytime I start FireFox/Mendeley/you name it.

Workaround/fix?

---

### Post by jeremy on 2011-05-01
I have the same problem with firefox and a few others.

---

### Post by ubnoobie on 2011-05-02
Thanks for the confirmation. Don't know what to do with that, yet, though...
___

Tried to get around the whole Unity crap by opting for XFCE (Xubuntu) instead, but XFCE appears to have its own annoying usability issue: configured titlebar doubleclick action (e.g. maximize, by default), **doesn't work right**. That one appears to be an issue where doubleclick timing on titlebar (only) is much, *much shorter* than the configured XFCE setting (it basically doesn't work because you have to set doubleclick timing so slow it's unusable elsewhere, just to get reasonable timing for titlebar action)

---

### Post by Anilix on 2011-05-02
More for me.

Pidgin, Gwibber skype and various others, when not maximized tend to "travel" rightways every time I recall them from the minimized or maximized state

---

### Post by Krytarik on 2011-05-02
> **Anilix said:**
> 
Pidgin, Gwibber skype and various others, when not maximized tend to "travel" rightways every time I recall them from the minimized or maximized state
I'm running Lucid 10.04., and I have that behaviour when I recall certain apps from the notification area, namely SMPlayer and Vagalume, but they 'travel' down, unless, of course, I set up rules for them in the "Place Windows" plugin, which I did for window size reasons. But particularly for Pidgin that's not the case. And I also didn't have that behaviour when I recall usual tasks.

So, maybe it's one of the newly added plugins in Compiz' "Window Management" category,

- the prime suspect is

[LIST]
[*]"Grid",
[/LIST]
- the rest, as a matter of completeness, are

[LIST]
[*]"Group and Tab Windows"
[*]"Extra WM Actions"
[*]"Maximumize"
[*]"Shelf".
[/LIST]

---

### Post by dpiddyTx on 2011-06-30
Anyone try submitting a bug for this yet?

---

### Post by georgelab on 2011-06-30
I noticed that a few weeks ago... Real bug so...

Reporting in!

---

### Post by mlnease on 2011-08-15
Getting on the bandwagon--still having the same problem (new windows default to maximized regardless of previous size & position) in Natty/Unity as of 8/15.

---

### Post by coffeecat on 2011-08-16
> **mlnease said:**
> Getting on the bandwagon--still having the same problem (new windows default to maximized regardless of previous size & position) in Natty/Unity as of 8/15.

That is not what the OP was complaining about, but I can help you with this. There is a threshold - 75% if I remember correctly - above which an unmaximised window will reopen maximised. Let me phrase that another way. If you unmaximise an application and resize it to greater than 75% of its maximised size, then it will open maximised when you reopen it. If you size the unmaximised window to less than 75%, then it will reopen the same size (unmaximised) as before.

Some people find the somewhat arbitrary 75% to be too small. So in Oneiric (which will be released in October) you will be able to adjust the threshold to your own liking in compizconfig-settings-manager. I find 80% to be about right for my purposes, but this is not possible in Natty/11.04 You are stuck with 75%.

With regard to the position of re-opening windows, there are a few misbehaving apps. I don't think it's a specific Unity bug, but I don't remember the details.

---

### Post by mlnease on 2011-08-16
> **coffeecat said:**
> That is not what the OP was complaining about, 

Right--sorry--

> **coffeecat said:**
> but I can help you with this. There is a threshold - 75% if I remember correctly - above which an unmaximised window will reopen maximised. Let me phrase that another way. If you unmaximise an application and resize it to greater than 75% of its maximised size, then it will open maximised when you reopen it. If you size the unmaximised window to less than 75%, then it will reopen the same size (unmaximised) as before.

Some people find the somewhat arbitrary 75% to be too small. 

I'd just say, 'too arbitrary'.

> **coffeecat said:**
> So in Oneiric (which will be released in October) you will be able to adjust the threshold to your own liking in compizconfig-settings-manager. I find 80% to be about right for my purposes, but this is not possible in Natty/11.04 You are stuck with 75%.

With regard to the position of re-opening windows, there are a few misbehaving apps. I don't think it's a specific Unity bug, but I don't remember the details.

Thanks for the explanation and for the news about Oneiric.  Looking forward to it.

---

### Post by spielball on 2011-12-17
Unfortunately, this compiz setting doesn't provide any solution for the fact that the windows' positions are not remembered by compiz. I'm frustrated. Not even the simplest things, that should be self-understood for an OS, work.

---

