---
title: "Window focus does not work properly"
date: 2010-08-19
forum: Desktop Environments
---

### Post by matteosistisette on 2010-08-19
Hi,

I have Ubuntu 10.04 installed and I haven't touched anything apparently relevant in its configuration.

Many times, when an application opens a new window and this should receive focus, it doesn't.

For example, i'm in Mozilla Thunderbird and I click on "Write" to write a new message, and I keep waiting, "why does it take so much to open???" - until I realised that the new message window was immediately opened but it didn't get focus, it is just blinking (in a barely pereivable way) in the panel on the bottom and I have to click on it to give it focus.

It is not just Thunderbird - just about any program, but not always.

Sometimes the same happens when switching some Flash Player web application to fullscreen mode (such as YouTube or MegaVideo): the full screen does not appear, I have to click on the icon on the panel on the bottom.

Sometimes, even more weired behaviour are observed. For example, let's suppose I have windows A, B and C open and none of them is minimized. I'll call "icon" a window's button on the bottom panel.
I click alternatively on icons of windows A, B, C, A, B, C and so on.
Expected: every time I click on a window's icon, the window should get focus and be brought to the front.
Observed: when I get to window A, it TOGGLES its state from open to minimized and viceversa, that is, when I switch from C to A, it does as if I was already on A, so instead of bringing it to front, it minimizes it; then next time I come back to A, it gets restored.

**In the overall, the windows' behaviour just seem completely ****ed up.** You click on a window's icon, you create a window or whatever and you just can't tell what's going to happen.


Is this some known bug, or is there some configuration option that I can try to change (which must have some insane default value if this is the expected behavior)??

thanks
m.

---

### Post by mcduck on 2010-08-19
Do you have visual effects enabled?

In that case install CompizConfig Settings Manager (if you haven't got it already), and then under General Options go to "Focus & Raise Behaviour"-tab and make sure the "Focus Prevention Level" is set to "Low" or "Off".

---

### Post by matteosistisette on 2010-08-19
> **mcduck said:**
> Do you have visual effects enabled?


No, they are disabled (in System/appearance, "visual effects" tab, "none" is selected).

---

### Post by mcduck on 2010-08-19
Ok. In that case check the options in System/Preferences/Windows, if you haven't done that already. If the window manager is set to focus on mouse and autoraise is enabled it *could* cause some windows to not appear on top as you'd expect them to. (you click on something to open a new window, but the mouse moves over another window focusing it and raising it to top, leaving the new window behind it)

edit: what comes to clicking a window button in the Window List applet, if the window in question is currently focused then clicking on the button is supposed to hide it, if the window isn't focused then clicking on the button focuses it. (and clicking on the button for a hidden window should, of course, unhide it).

---

### Post by matteosistisette on 2010-08-19
> **mcduck said:**
> Ok. In that case check the options in System/Preferences/Windows, if you haven't done that already. If the window manager is set to focus on mouse and autoraise is enabled 

Hi, thank for your help and for replying so quickly.

Under System/Preferences/Windows, the option "Select windows when the mouse moves over them" is **not** checked (and the "autoraise" option is unchecked and greyed out). And indeed moving the mouse over windows does not give them focus.

Btw that when I click on the menu item "windows" in System/Preferences, and the "Window Preferences" window is opened but on the background, as usual (and its button on the bottom panel blinks).

---

### Post by matteosistisette on 2010-08-19
> **matteosistisette said:**
> 
Btw that when I click on the menu item "windows" in System/Preferences, and the "Window Preferences" window is opened but on the background, as usual (and its button on the bottom panel blinks).

But not always.

---

### Post by mcduck on 2010-08-19
> **matteosistisette said:**
> Hi, thank for your help and for replying so quickly.

Under System/Preferences/Windows, the option "Select windows when the mouse moves over them" is **not** checked (and the "autoraise" option is unchecked and greyed out). And indeed moving the mouse over windows does not give them focus.

Btw that when I click on the menu item "windows" in System/Preferences, and the "Window Preferences" window is opened but on the background, as usual (and its button on the bottom panel blinks).

OK. In that case I really have no idea what could be the problem, as those are the only settings that control the window behaviour.

Sorry, but it seems that you'll just have to wait and see if somebody else has more ideas what could cause your problem.

---

### Post by darrencook on 2011-11-08
I think I have the same problem, also using ubuntu 10.04 and gnome.

It has been driving me crazy for a year now; I've always suspected it was something to do with mouse behaviour because the temporary fix has always been to right-click. The first right-click does nothing and then the second brings up the pop-up, and it is okay.
But it soon happens again; closing all windows never works (the problem is there when I start something again) so it is not caused by an application. The only fix is to logout and login again. Then everything is working fine for another few hours or days.
BTW, using ctrl-alt-F1, etc. to switch to a commandline session and back again does not fix it. (That trick has fixed X-related problems for me.) So, I suspect a gnome bug.
As far as filing a bug report goes, I've not worked out what the trigger is. I cannot reproduce the problem on demand. Just wait a few hours for it to appear again.

Anyway, I realized today the problem could be described as windows failing to get focus properly. That led me to this thread. Clicking a window does not bring it to the front (and keypresses still go to previous window). Right-clicking on the window gives it focus. But also using alt-tab gives it focus.

I also have compiz effects all turned off. And under Windows Preferences the "Select windows when the mouse moves over them" box is not checked.

---

