---
title: "Loss of application focus and unwanted menu closure"
date: 2009-05-01
forum: General Help
---

### Post by imbjr on 2009-05-01
First I knew something was up was when I was running Forte Agent under WINE. Occasionally, I'd notice that the mousewheel appeared to no longer work as I was attempting to scroll a list of usenet messages. But then I noticed that the message pane had lost focus. In fact, one can watch the top-left icon go grey after a short while when it does this.

Next, I noticed that Firefox's menus were affected. If one is navigating through the bookmarks menu and sub-menus and taking a little while about it, suddenly the whole series of menus will vanish. Other applications do this, for example Google Earth, but not not the entire menu hierarchy. Some apps don't do it, such as gedit.

Eventually, these effects stopped ...

At first I thought a reboot/restart was resetting something so it no longer happened, but now I believe some process is running for a period (maybe an hour) and then stopping. It only does this for the first boot of the day too.

Anyone experienced this? Anyone know of a possible process culprit?

Tomorrow I shall ps -elf at the start and then do again once I'm certain the effect has stopped again. Hopefully, something will show.

---

### Post by imbjr on 2009-05-08
Well it's doing it again. Mmmm, was it last Friday that this happened?

Time to ps -elf ...

---

### Post by imbjr on 2009-05-08
Looks like a re-login fixes the problem.

I've generated a ps -elf listing again for future comparison.

Note: VirtualBox was probably running in both periods, this time and last time when this happened, and quite possibly in both occasions new virtual OS installations were being setup.

---

### Post by imbjr on 2009-05-11
Yes, a re-login fixes it.

Also: I happened to move the mouse cursor to Agent's menu when the mousewheel focus was lost - and up pops the menu that was under the cursor. So this made me suspect the alt key.

It's as if the alt key is being pressed. I know that underneath my keys its quite dirty, but I can't see why a re-login fixes the problem.

Pressing the alt key is what also cancels the Firefox menu when it's displayed.

But what could be issuing these alt keypresses?

---

### Post by imbjr on 2009-05-18
Well, it looks as if Totem is the problem:

[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/216939](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/216939)

Fortunately, this rather bad implementation of screensaver prevention can be turned off in the preferences for Totem.

---

