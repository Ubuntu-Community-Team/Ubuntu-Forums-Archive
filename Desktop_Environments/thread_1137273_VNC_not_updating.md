---
title: "VNC not updating"
date: 2009-04-25
forum: Desktop Environments
---

### Post by Tass on 2009-04-25
I've recently upgraded from Intrepid to Jaunty, and am having some issues with the display drivers.

The first issue has now been resolved - I had to reinstall xserver xorg.  The underlying issue I'm trying to resolve is the default resolution of ubuntu when running without a screen attached, but when I VNC in, VNC doesn't update the screen at all. 

My mouse movements work, but anything that would affect the rest of the screen, nothing happens.  Keypresses are the same.  If I disconnect & reconnect, the action I performed and didn't see has happened.  This is excruciating, trying to navigate round the menus, edit config files, etc.

Any ideas?

---

### Post by phibit on 2009-04-25
I have this same problem. When I connect to my desktop with VNC, the actions performed remotely are executed on the server PC, but the display on the vnc client isn't updated to correspond.

I also am experiencing this problem after upgrading from intrepid to jaunty, and I'm a bit confused.

---

### Post by Tass on 2009-04-25
Excellent - so not just me going insane!  Sounds like a specific Jaunty issue - hopefully someone will be sorting it out soon!!

---

### Post by phibit on 2009-04-25
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/353126](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/353126)

Seems like we're not the only ones. And it seems like this bug is specific to the new nvidia drivers + compiz + vino-server.

Suggested workaround is to disable compiz (--metacity replace).

---

### Post by phibit on 2009-04-25
I can confirm that this is an nvidia + compiz + vnc issue for me, or at least that it's compiz.

Using metacity as a window manager fixed my problem.

---

### Post by mloquercio on 2010-02-16
Maybe this is too beginner for this thread, but I uninstalled compiz using synaptic (graphical package manager) and am still having a problem.  Any advice?

---

