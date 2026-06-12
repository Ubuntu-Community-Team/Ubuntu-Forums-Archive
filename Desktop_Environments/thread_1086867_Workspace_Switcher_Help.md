---
title: "Workspace Switcher Help"
date: 2009-03-04
forum: Desktop Environments
---

### Post by Beguiler on 2009-03-04
Hooray, first post. 

This is probably a stupid question. I'm new to Ubuntu though. And it's probably answered somewhere. But damn it all, I can't find it.

My laptop has Ubuntu 8.10. I love it. 
But, the laptop had some problems with the fglrx that I installed. Finally fixed that issue (seems I didn't have an ATI card new enough), but when I finally booted up, everything worked fine.

Except the workspace switcher. At first, clicking on it simply did nothing. Right clicking showed that it was still recognized as a workspace switcher, but it didn't work.

 Got Compiz, haven't done much in it. According to a few of the threads I have browsed, this problem is simple. And I quote...

Go to your CompizConfig Settings Manager and under General Options->Desktop Size,

Horizontal Virtual Size: 4
Vertical Virtual Size: 1
Number of Desktops: 1
(End quote)

When I hold the alt+ctrl, and start hitting directions, only the up or down does anything. Which is shrink my desktop size on the y-axis, and then show two other desktops, one on either side. Pressing over does nothing. Releasing ctrl or alt brings the desktop back to normal.

Any ideas? I'm lost.

Thanks.

---

### Post by kanikilu on 2009-03-04
Do you have the Desktop Cube and Rotate Cube plugins enabled? You can set the key bindings in the Rotate Cube plugin to suit your preference.

I believe you can also change the default metacity keybindings in gconf-editor, browse to /apps/metacity/global_keybindings, the values you want are switch_to_workspace_[1-4].

---

### Post by Beguiler on 2009-03-04
You are my savior. I knew it was something pretty simple. Usually is.

Many thanks. Yes, the above response did fix my problems.

---

