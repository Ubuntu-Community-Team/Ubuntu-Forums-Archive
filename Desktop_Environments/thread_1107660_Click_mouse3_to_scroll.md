---
title: "Click mouse3 to scroll"
date: 2009-03-27
forum: Desktop Environments
---

### Post by TheNTW on 2009-03-27
Hi,
I was thinking about this for a very long time, and now it is time to ask I think :)

So - How do I re-bind buttons on my mouse ? What I need exactly is to bind mouse3 button (wheel) To enable "scrolling mode" and page for instance in FireFox is scrolling up/down/left/right depending on what direction do I move my mouse.
I remember when I was using Win I got really used to this function.

So, any help ?

---

### Post by mcduck on 2009-03-27
Actually the wheel click is button 2 ;)

There is no support for autoscrolling with the middle click, probably because it's traditionally used for so many other purposes on Unix/Linux systems.

But if you want, you can still enable it in Firefox:

Type "about:config" as the address, then use "scroll" as filter to find the key called "general.autoScroll".  Right-click that and select "Toggle" to change the key's value to "true".

---

### Post by TheNTW on 2009-03-28
Thank you!
This is perfect :)


p.s. For what other purposes can mouse2(?) be used in unix ?  :)

---

### Post by mcduck on 2009-03-28
For example the normal copy/paste method in Linux is to select the text you want to copy, and then just middle-click where you want to paste it. (works great for terminals, for example, as Ctrl-C has a completely different meaning there).

You can also use Alt+middle button to resize a window from any point in the window (as opposed to just the window borders). Alt-left button works in the same way, only moving the window instead of resizing it.

May minimalistic window managers have their own uses for middle button as well. Openbox doesn't have any panels, so there's no task list or anything to show your virtual desktops or minimized applications. Instead, middle click opens a nice popup menu that lists all your desktops and running programs.

---

