---
title: "Terminal Server Client Exit Fullscreen - Won't lose focus"
date: 2007-10-28
forum: Desktop Effects &amp; Customization
---

### Post by techstop on 2007-10-28
OK, I am posting this in here because I think the problem is related to Compiz. I connect to a Windows server at work using the Terminal Server Client GUI. Normally you press Ctrl + Alt + Enter to exit fullscreen. When I do that you can see the borders of the windows doing the minimise animation in Compiz, but the remote session does not lose focus and stays on top in fullscreen. Anyone else with this problem?

EDIT: Solved by handspringer in post #7. Solution is to disable fullscreen legacy support in ccsm under "Workarounds".

---

### Post by cagliano on 2007-10-29
I do have the same problem.

quite annoying because I use terminal server a lot..
and I do like compiz effects :-)

---

### Post by Dexter73 on 2007-10-30
I noticed this,too.

And I think you are quite right that this is compiz related. If you change to metacity, Ctrl-Alt-Enter works just fine.

---

### Post by techstop on 2007-10-30
There are a couple of bugs listed on launchpad. Hopefully it will get fixed ASAP because it's a pretty serious issue. Can't believe it wasn't picked up during the beta tests...

---

### Post by cagliano on 2007-10-31
> **Dexter73 said:**
> I noticed this,too.

And I think you are quite right that this is compiz related. If you change to metacity, Ctrl-Alt-Enter works just fine.

I agree, same behaviour for me

metacity = works fine
compiz = don't lose focus

bye

---

### Post by agramata on 2007-11-04
In my standard install of Gutsy (with Compiz), it looks like alt+ F9 is mapped to minimize in Compiz. Give that a shot, it seems to work for me.

EDIT - after re-reading the original post, it seems the OP wanted not to minimize the window, but knock it from fullscreen to windowed mode. My suggestion above minimizes it. Still helpful since ctl+alt+enter does not work, but not a real solution to get it into windowed mode. Apologies.

---

### Post by handspringer on 2007-11-07
I had the same problem (Won't lose focus).
Here's the way, how I solved it:

1. The <Advanced Desktop Effects Settings (ccsm)> tool to configure your compiz settings have to be installed.

2. Start this tool under SYSTEM -> PREFERENCES

3. Under the category UTILITY -> WORKAROUNDS you have to deactivate the <Legacy Fullscreen Support> which makes Wine and legacy applications fullscreen properly.

This solved my fullscreen problem.

Hope it solves yours....

PS: This is my first post ever. I hope, it works :)

---

### Post by techstop on 2007-11-07
Thanks guys for the tips. I am off work for a couple of weeks for exams, I'll test them out when I get back. I'll let you know how I go... :)

---

### Post by GlennB on 2007-11-10
Hi All,

I'm glad I found this thread - rdesktop was driving me mad since I installed Gutsy! The mod to the Compiz workarounds works for me.

On a related subject, is anyone else having trouble with the "Aternate full screen" option in the terminal client GUI? It seems to feed rdesktop with an invalid option "-F", which I'm guessing should be a lower case "f" rather than uppercase. Whenever I check this option the app. issues an error. Can anyone confirm?

Thanks,

Glenn.

---

### Post by jlbauer on 2007-11-17
Am having same problem. Full screen mode causes error: invalid switch -F. Works fine using default screen size.

---

### Post by techstop on 2007-11-20
> **handspringer said:**
> I had the same problem (Won't lose focus).
Here's the way, how I solved it:

1. The <Advanced Desktop Effects Settings (ccsm)> tool to configure your compiz settings have to be installed.

2. Start this tool under SYSTEM -> PREFERENCES

3. Under the category UTILITY -> WORKAROUNDS you have to deactivate the <Legacy Fullscreen Support> which makes Wine and legacy applications fullscreen properly.

This solved my fullscreen problem.

Hope it solves yours....

PS: This is my first post ever. I hope, it works :)

Thanks for the tip, it works! Great first post btw!

Cheers....I'll mark this as solved...

---

### Post by bobby.hawk on 2007-12-19
> **handspringer said:**
> I had the same problem (Won't lose focus).
Here's the way, how I solved it:

1. The <Advanced Desktop Effects Settings (ccsm)> tool to configure your compiz settings have to be installed.

2. Start this tool under SYSTEM -> PREFERENCES

3. Under the category UTILITY -> WORKAROUNDS you have to deactivate the <Legacy Fullscreen Support> which makes Wine and legacy applications fullscreen properly.

This solved my fullscreen problem.

Hope it solves yours....

PS: This is my first post ever. I hope, it works :)

Under System -> Preferences -> Utility (I don't have Utility)
How I get that?

Bob

---

### Post by techstop on 2007-12-20
> **bobby.hawk said:**
> Under System -> Preferences -> Utility (I don't have Utility)
How I get that?

Bob

To clarify, you need to go into the following menu from your GNOME desktop;

System > Preferences > Advanced Desktop Effects Settings

When you have opened that, THEN you need to go into the following menu of that application;

Utility > Workarounds

If you have ccsm installed, I can't see why you wouldn't have that menu item.

---

### Post by ocr14a on 2008-01-15
:confused: + post 7 = :)

Thanks a bunch!!

---

### Post by MountainX on 2008-01-21
I hope no one minds me asking a related question. After I exit full screen mode, how do I get back into full screen mode?

Thanks for the great tip on compiz and exiting full screen RDP mode.

---

### Post by ocr14a on 2008-01-22
I just do the Ctrl+Alt+Enter again (with the rdp session in focus) and it returns to full screen.

Is that what you mean?

---

### Post by MountainX on 2008-01-22
> **ocr14a said:**
> I just do the Ctrl+Alt+Enter again (with the drp session in focus) and it returns to full screen.

Is that what you mean?

YES!!! That's perfect! Thank you so much. As obvious as this seems, I didn't think of trying that.

---

### Post by BassKozz on 2008-02-19
Thanks handspringer :popcorn:

---

### Post by BassKozz on 2008-02-20
Now only if there were a way to switch workspaces (ctrl+alt+left or right) w/out having to minimize (ctrl+alt+enter) ?
That way you could have one rdesktop session running in each workspace and you could switch between them seamlessly using ctrl+alt+left or right, w/out having to 1st ctrl+alt+enter then ctrl+alt+left or right.
I guess in the grand scheme of things it's only an extra keystroke, but it still sure would be nice ;)

---

### Post by BassKozz on 2008-02-22
> **B/-\ssKozz said:**
> Now only if there were a way to switch workspaces (ctrl+alt+left or right) w/out having to minimize (ctrl+alt+enter) ?
That way you could have one rdesktop session running in each workspace and you could switch between them seamlessly using ctrl+alt+left or right, w/out having to 1st ctrl+alt+enter then ctrl+alt+left or right.
I guess in the grand scheme of things it's only an extra keystroke, but it still sure would be nice ;)

Found a solution thanks to Gerhard on the [rdesktop Mailing List](http://sourceforge.net/mail/?group_id=24366) :
> Fullscreen mode automatically disables local window manager shortcuts,  but you can start it in a window without window decorations with the geometry of your screen. You also set an option to keep your window manager key bindings.
```
rdesktop &#8211;D &#8211;g 1280x1024+0+0 &#8211;K server
```-GES

---

### Post by phil511 on 2008-04-13
> **handspringer said:**
> I had the same problem (Won't lose focus).
Here's the way, how I solved it:

1. The <Advanced Desktop Effects Settings (ccsm)> tool to configure your compiz settings have to be installed.

2. Start this tool under SYSTEM -> PREFERENCES

3. Under the category UTILITY -> WORKAROUNDS you have to deactivate the <Legacy Fullscreen Support> which makes Wine and legacy applications fullscreen properly.

This solved my fullscreen problem.

Hope it solves yours....

PS: This is my first post ever. I hope, it works :)

I had the same problem.
Thank you handspringer, your solution works for me. But I'm wondering why this option is enabled by default? Is there any drawbacks by disabling it?

---

