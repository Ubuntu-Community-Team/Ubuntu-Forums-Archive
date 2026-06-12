---
title: "cursor disappears in Terminal"
date: 2016-02-01
forum: Desktop Environments
---

### Post by davidmaxwaterman on 2016-02-01
Hi,

Can someone tell me how to stop the cursor from disappearing in the Terminal? I'm talking about the mouse cursor, not the terminal prompt. It doesn't stop me from typing, but it makes me think the window doesn't have focus. A click of the mouse restores it, but the experience overall is frustrating.

I'm not entirely sure what causes it, but it isn't consistent. Potentially relevant peculiarities of my setup at that I have focus follows mouse.

Anyone seen this before? A search suggests that some people have seem similar behaviour but not recently.

Max.
15.10

---

### Post by oldos2er on 2016-02-01
What terminal are you using?

---

### Post by sergey39 on 2016-02-02
> **davidmaxwaterman said:**
> Hi,

Can someone tell me how to stop the cursor from disappearing in the Terminal? I'm talking about the mouse cursor, not the terminal prompt. It doesn't stop me from typing, but it makes me think the window doesn't have focus. A click of the mouse restores it, but the experience overall is frustrating.

I'm not entirely sure what causes it, but it isn't consistent. Potentially relevant peculiarities of my setup at that I have focus follows mouse.

Anyone seen this before? A search suggests that some people have seem similar behaviour but not recently.

Max.
15.10

I have the same issue. The patter to reproduce is:
Open Terminal, focus it, move mouse over the terminal window (so the cursor transforms to text selection type), press enter : cursor disappears.

Sergey

---

### Post by davidmaxwaterman on 2016-02-02
> **oldos2er said:**
> What terminal are you using?

The one called 'Terminal' from the 'Launcher'.

Max.

> **sergey39 said:**
> I have the same issue. The patter to reproduce is:
Open Terminal, focus it, move mouse over the terminal window (so the cursor transforms to text selection type), press enter : cursor disappears.

Sergey

Yeah, that looks the same thing to what I'm seeing...didn't realise it was so simple to reproduce.

Max.

No one has a solution? Do we think it's a bug of some sort?

I wonder if it's a symptom of the colour/theme - ie the cursor goes to black-on-black for some reason. @sergey39 what colours are you using? I have green text on black background...'Green on black' in the Preferences/Profiles->Unnamed->Edit->Colours/Built-in schemes panel, with the Rxvt 'Built-in schemes' Palette.

---

### Post by nelo-onyiah on 2016-02-04
I have the same problem using the default terminal on a fresh install of Ubuntu 15.10.

---

### Post by davidmaxwaterman on 2016-02-04
> **nelo-onyiah said:**
> I have the same problem using the default terminal on a fresh install of Ubuntu 15.10.

I don't suppose anyone has logged a bug on this? Where would one do that, I wonder...

Max.

---

### Post by mc4man on 2016-02-05
What is the bug here? There never is a "cursor" in the terminal, just the I-beam. So while  it disappears after running a command, it comes back with any activity within the terminal.

---

### Post by davidmaxwaterman on 2016-02-05
> **mc4man said:**
> What is the bug here? There never is a "cursor" in the terminal, just the I-beam. So while  it disappears after running a command, it comes back with any activity within the terminal.

(I'm going to switch from calling it 'cursor' to calling it a 'mouse pointer', since I also need to refer to the cursor on the command line)

There is normally a mouse pointer in the terminal. If I move it from this window (chrome) over the top of the terminal, it is still there and I can see that the terminal now has focus because the window border changes colour, the menu appears on the top of the window, and the command line cursor changed from an outlined rectangle to a filled one.

When this bug occurs, that doesn't happen, and I end up waving the mouse around trying to locate the mouse pointer with my eye...it is extraordinarily frustrating and irritating when it happens.

What you write - 'There never is a "cursor" in the terminal, just the I-beam' - is, to me, clearly not correct, so I presume I'm not explaining it well enough. I suppose there is the possibility of "it's supposed to be like this" and I just don't "get" why...

---

### Post by mc4man on 2016-02-05
Well basing on you agreeing with steps to reproduce in post 3, that just seems like normal behaviour here, seen in both a terminal & text editor.
(- to get past syntax attached quick vid, cursor/mouse pointer changes to I-beam when in either window, pressing enter in either window makes the I-beam disappear, activity of any sort returns.
 

On the other hand every once & a while (rare here) when moving the 'cursor/mouse pointer' over a terminal I get nothing. This is not reproducible from any recipe, it just happens... Is that more like what you mean?

---

### Post by kalman-ondrej on 2016-02-08
This is really annoying especially if you use more than one display. When you move mouse from one display to other on which is opened terminal and you can find your cursor.

---

### Post by sergey39 on 2016-02-09
> **mc4man said:**
> Well basing on you agreeing with steps to reproduce in post 3, that just seems like normal behaviour here, seen in both a terminal & text editor.
(- to get past syntax attached quick vid, cursor/mouse pointer changes to I-beam when in either window, pressing enter in either window makes the I-beam disappear, activity of any sort returns.
 

On the other hand every once & a while (rare here) when moving the 'cursor/mouse pointer' over a terminal I get nothing. This is not reproducible from any recipe, it just happens... Is that more like what you mean?

To reproduce the "once & a while" you have to follow the same pattern as post #3 with an additional step : after the mouse pointer disappeared focus other window. Now when your mouse hovers console it becomes invisible (even when not focused).

P.S. for mouse to disappear you can press any key when in terminal and not only "enter"

---

### Post by vdmit on 2016-02-29
I have fresh installation of Ubuntu 15.10 and I'm experiencing exactly same issue. Very annoying indeed!

---

### Post by Frode_Underhill on 2016-03-11
Same or similar problem here (Ubuntu 15.10). In my case, the cursor seems to only disappear if there is some activity in the terminal.

Judging by [this superuser thread]("https://superuser.com/questions/902909/disabling-mouse-hiding-in-gnome-terminal-while-typing"), the cursor's disappearance is apparently a result of gnome-terminal's "hide while typing" feature. Normally, it should reappear when the mouse is moving, but a bug is preventing it. The bug is allegedly fixed in the newest Gtk version.

---

### Post by davidmaxwaterman on 2016-04-04
This is still bugging me. I think it might well be some kind of 'feature' where it attempts to declutter the screen when you're using a terminal. However, this idea doesn't work at all when the user has 'focus follows mouse' as I do.

For example, I am now typing into chrome, but the terminal has a solid cursor which implies *it* has focus, when it clearly does not - so I can't use that to tell where the cursor is.

If I move the mouse pointer over the terminal and click, it disappears, and I get focus...fair enough. However, it I alt-tab back to my chrome window, then the chrome window has focus, but the mouse pointer is still invisible.

There really needs to be a way to turn off this 'hide the mouse pointer' feature.

---

### Post by davidmaxwaterman on 2016-04-04
I filed a bug on this :

[https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/1565846](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/1565846)

Note that, while filing the bug, everything returned to normal, so it is clearly some situation where things 'go wrong'. I am also doubting it is related to my use of focus-follows-mouse and click-to-raise==off, and more to do with alt-tab; but I'm not at all clear.

---

