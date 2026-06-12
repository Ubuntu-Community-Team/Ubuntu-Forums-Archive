---
title: "How to move a window quickly"
date: 2005-11-25
forum: Desktop Environments
---

### Post by jlist on 2005-11-25
I find that on KDE if I want to click on and drag a window title to move the window, I have to hold down the mouse on the window title for a few seconds until the cursor becomes a little grabbing hand. Then I can move the window. Before than I won't be able to move the window. This is annoying to me because if I want to rearrange the desktop, which involves moving quite a few windows, I'll have to wait for a few seconds for each of them. I checked the settings in "System Settings" but didn't find anything that changed this behavior. Any hints?

---

### Post by ajgreeny on 2005-11-25
[QUOTE=jlist]I find that on KDE if I want to click on and drag a window title to move the window, I have to hold down the mouse on the window title for a few seconds until the cursor becomes a little grabbing hand. Then I can move the window. Before than I won't be able to move the window. This is annoying to me because if I want to rearrange the desktop, which involves moving quite a few windows, I'll have to wait for a few seconds for each of them. I checked the settings in "System Settings" but didn't find anything that changed this behavior. Any hints?[/QUOTE]

I've got both Hoary and Breezy on my machine and on both versions there is no problem like the one you mention.  On both as soon as i left click on the title bar the hand appears and I can move the window with no delay at all.  What is the spec of your machine, and could it be anything to do with slow graphics or a mouse problem?

---

### Post by jlist on 2005-11-25
I'm running it in a vmware, so, not extremely fast. But the host OS runs on a Pentium M 1.7G so the guest OS is not slow at all. Graphics works just fine. I also ran ubuntu in vmware on a much slower PC and gnome doesn't have that problem. I still suspect it's due to a system setting.

---

### Post by thingy on 2005-11-26
Can you confirm where Control Center\Peripherals\Mouse\Advanced doesn't have weird values for the Drag click and start time intervals.

Click should be 400 msec and start should be 500msec.

Other than the above, I'm at a loss as to what this could be.A vmware quirk?

---

### Post by jlist on 2005-11-27
The drag start time setting is 300ms. I changed it to 100ms or 0 ms and it didn't make a difference.

ubuntu (gnome) running in vmware on a slower machine doesn't have this problem. I think it's still a KDE issue.

---

### Post by f1dave on 2005-11-27
Personally, I would find it much more likely to be a VMware quirk with KDE than a KDE issue itself- much the same as if you have problems running Diablo 2 in cedega, the problems are quirks in cedega- not problems with the game.

---

### Post by bailout on 2005-11-27
I find the same problem under both kde and gnome. I click and move as I am used to under windows and fail to pick up the window. It is frustrating.

---

### Post by xelink on 2005-11-27
make sure the window isn't maximized... drags fine when isn't, but when it is, you have to wait a moment.

also, try pressing alt and dragging from anywhere on the window when it isn't maximized.

---

### Post by jlist on 2005-11-27
[QUOTE=bailout]I find the same problem under both kde and gnome. I click and move as I am used to under windows and fail to pick up the window. It is frustrating.[/QUOTE]
That's right. It's actually happening on gnome, too but it seems better on gnome. I'm also from the Window camp. It works very well on Windows and that's how I notice that it's kind of annoying on KDE. Well, you can also say frustrating.

To xelink: no. they are not maximized windows.

---

