---
title: "Ubuntu logo on the Gnome 3 panel - a tip!"
date: 2011-10-28
forum: Desktop Environments
---

### Post by tpprynn on 2011-10-28
Before Gnome 3.2 there was a gnome-shell-extension that would put a distro logo on the panel next to Activities. It bugged me that whether we used Ubuntu, Fedora or Sabayon etc there was no branding, so I've looked into a workaround.

If you open /usr/share/gnome-shell/theme as root, dump the files attached here in there and reboot and you will have your unhomogenised Gnome 3 desktop... The css file is almost the same as the one it replaces (you'll have to okay it being replaced) in this folder but with about six lines added.

Apologies if you like yours the way it is!

---

### Post by BlinkinCat on 2011-10-28
Hi,

A little off topic - but how do you get the month and the date in the top panel? - I see them in the system settings but can't see how they are adjusted -
Can you help me out?

Cheers - :)

Edit - also I didn't think gnome 3 had graphics for its trash?

---

### Post by tpprynn on 2011-10-28
You need the new Gnome Tweak Tool, where you'll soon see how both of those are done.

sudo apt-get install gnome-tweak-tool

In the dash it's named Advanced Settings, probably in the top row.

---

### Post by BlinkinCat on 2011-10-28
Aha - Thanks very much for that tpprynn - I've only just installed gnome 3 and am still learning -

Thanks again - :P

---

