---
title: "Disappearing Panel"
date: 2010-06-21
forum: Desktop Environments
---

### Post by robobart on 2010-06-21
Sometimes on login my Gnome Panel is missing.

I've been running Ubuntu since 6.04 and haven't seen stuff like this. Did 10.04 come out too soon??

Thanks!

---

### Post by wilee-nilee on 2010-06-21
> **robobart said:**
> Sometimes on login my Gnome Panel is missing.

I've been running Ubuntu since 6.04 and haven't seen stuff like this. [B]Did 10.04 come out too soon??
[/B]
Thanks!

This post will not help you get any answers, be more specific.

---

### Post by robobart on 2010-06-21
Sorry - 

when the panel disappears, I try:

alt-f2

and then 

gnome-panel

but the panel does not appear. 

Any thoughts as what could be causing this?

---

### Post by wilee-nilee on 2010-06-21
I don't have any answers other then we don't know any tweaking you might have done to your OS, or if the install was just not a clean one, or if it is driver issue of some sort.
I don't think that command is a correct one. You might just try setting the startup applications 2nd tab to save sessions when you have the panel showing.

```
killall gnome-panel
```
will probably restart it even when not seen, then save the session.

Here is a link that may help.
[http://www.yolinux.com/TUTORIALS/GNOME.html](http://www.yolinux.com/TUTORIALS/GNOME.html)

I think your problem is isolated to your setup, and none of us know what that setup is or as I said any tweaking you have done, but maybe if your lucky, somebody can help you.

---

### Post by robobart on 2010-06-21
I think your suggestion will work, 

But here is another clue. It happened again, so I used alt-f2 to start a terminal.

Then I tried to start the panel with 

gnome-panel

I got this back:

> Cannot register the panel shell: there is already one running.

then I decided to move my mouse all the way to the bottom of the screen and click around, after a moment, the panel appeared!

As far as tweaks are concerned, I am running a desktop terminal via devilspie (which also doesn't show up when this happens) but that is about it.

Thanks for the suggestions!

---

