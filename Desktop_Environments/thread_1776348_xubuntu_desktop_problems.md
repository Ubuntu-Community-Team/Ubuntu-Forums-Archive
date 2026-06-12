---
title: "xubuntu desktop problems"
date: 2011-06-06
forum: Desktop Environments
---

### Post by GreenBuffalo on 2011-06-06
I recently installed Xubuntu 11.04, Natty Narwhal, dual boot with Vista.   Until this evening, it's been terrific-- very fast and easy to  configure.

A couple hours ago I rebooted to test the session restore feature, and  the desktop is now very buggy.  Have rebooted two more times  with the same problems.  In particular:

- All new windows open in the upper left, covering the panel bar, and  offset upwards so that the grab edge of the window is offscreen.
- Settings manager--> window manager screen is empty.
- Active window doesn't foreground.  New windows just stack on top of  the old ones, and stay in that order even when I switch to a different  window.
- Number of workspaces reset to 1, and I can't open any more from Settings manager--> Workspaces.
- Context menus within windows are a little buggy-- after right  clicking, I need to use the arrow keys to select, otherwise the menu  disappears as soon as I move the mouse.

At this point, it wouldn't be too time-consuming to backup my data and  reinstall, but I'd like to know what happened so I can avoid it in the  future.  And if there's a way to fix this without reinstall, that would  be terrific.

I'm definitely not an experienced user, but can provide any info  necessary to diagnose the problem.  I do have a list of packages that I  installed/removed since installing.

I'd appreciate any help. Thank you very much in advance!

---

### Post by wildmanne39 on 2011-06-06
> **GreenBuffalo said:**
> I recently installed Xubuntu 11.04, Natty Narwhal, dual boot with Vista.   Until this evening, it's been terrific-- very fast and easy to  configure.

A couple hours ago I rebooted to test the session restore feature, and  the desktop is now very buggy.  Have rebooted two more times  with the same problems.  In particular:

- All new windows open in the upper left, covering the panel bar, and  offset upwards so that the grab edge of the window is offscreen.
- Settings manager--> window manager screen is empty.
- Active window doesn't foreground.  New windows just stack on top of  the old ones, and stay in that order even when I switch to a different  window.
- Number of workspaces reset to 1, and I can't open any more from Settings manager--> Workspaces.
- Context menus within windows are a little buggy-- after right  clicking, I need to use the arrow keys to select, otherwise the menu  disappears as soon as I move the mouse.

At this point, it wouldn't be too time-consuming to backup my data and  reinstall, but I'd like to know what happened so I can avoid it in the  future.  And if there's a way to fix this without reinstall, that would  be terrific.

I'm definitely not an experienced user, but can provide any info  necessary to diagnose the problem.  I do have a list of packages that I  installed/removed since installing.

I'd appreciate any help. Thank you very much in advance!
Hi, sorry I had the wrong information.

---

### Post by Bucky Ball on 2011-06-06
Xubuntu uses Xfce, *not* Unity.

---

### Post by Toz on 2011-06-06
Press Alt+F2, type in:```
xfwm4 --replace
```and click on "Run".

Does this help?

---

### Post by GreenBuffalo on 2011-06-06
Thanks Toz!  That did the trick.

(except Alt-F2 wasn't working, so I opened Accessories-->Terminal emulator.)

---

### Post by Toz on 2011-06-06
Great. Just to give you a heads up, to have xfwm4 startup next login, you're going to either have to logout and check the "Save Session" checkbox, or add xfwm4 to your startup programs.

And if you don't mind, can you mark this thread as Solved from the Thread Tools above?

---

### Post by GreenBuffalo on 2011-06-06
Done and done.  Thanks again.

---

### Post by GreenBuffalo on 2011-06-06
Just a follow up:  

Enabling "save session" isn't enough-- I had to add "xfwm4 --replace" to Settings manager--> Session and startup--> Application autostart.

Also, when the desktop is acting flaky, terminal windows will open but WON'T accept keyboard input.  You have to close all open windows, then open a terminal.

Lastly, "saved session" appears to just reopen all previous windows from all workspaces in workspace 1-- it doesn't return them to the previously assigned workspace.  That's a bit inconvenient, as I work with a lot of windows.  But I'll deal with that problem further down the road.

Again, thank you for the assistance!

---

