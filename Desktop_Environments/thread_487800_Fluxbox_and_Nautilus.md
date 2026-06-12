---
title: "Fluxbox and Nautilus?"
date: 2007-06-29
forum: Desktop Environments
---

### Post by Yonderknight on 2007-06-29
Hi everyone,

I installed ubuntu recently and I'm already hooked to getting everything the way I like. I installed fluxbox and have been experimenting with different programs for desktop icons.

So far I've tried iDesk, ROX filer, and nautilus (which was the default for gnome) and I gotta say nautilus is by far the most useful one I've used.

The problem is it doesn't have a "compatibility" mode like ROX does, if you try to right-click on the desktop your fluxbox menu doesn't show up =(. I've set a hotkey for the fluxbox menu though, so I can just use that, but I want a better way.

I was wondering if there's any way to get a "start button" to display the menu like in windows. 

Also, what desktops do you guys recommend? What things do you like or not like about them?

Thanks!

---

### Post by RedSquirrel on 2007-06-29
You have to run nautilus with the "--no-desktop" option to be able to right-click on the desktop to get the menu.

```
nautilus --no-desktop
```Unfortunately, that means no desktop icons with nautilus. There is something called fbdesk that can be used for desktop icons, but I have not used it myself.

There is a way to have a "start button" type of thing, but I've never used it so I can't remember what it's called. kerry_s was using something like that so he'll probably drop by with the answer at some point... :)

I just use bare Fluxbox SVN -- no rox or anything...


EDIT: wmdrawer might be a possibility.

---

