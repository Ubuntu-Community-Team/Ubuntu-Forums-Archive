---
title: "focus stealing"
date: 2015-07-21
forum: Desktop Environments
---

### Post by Martin_Mucha on 2015-07-21
Hi,

Currently I'm using XFCE, but this question is not strictly xfce related as I'm willing to adopt new environment, which solves this issue. 

My problem is, that I have to use apps, which steals focus from another window. If I click some icon, or invoke action, app window gets focus. The problem is, that given action sometimes takes lets say 30s. And since I do another work meantime, when focus got switched, I continue writing in another window, confirming unwanted actions (even if I do not look at keyboard while writing, I still pressed 'cancel' so many times ...)

The only solution I know, is to forbid that and changing focus with mouse, but that doubles clicking for most of actions ~ start chrome, give focus to it — for example. Is there a better solution to it? Like blacklisting apps which cannot steal focus, or "app can request focus only if there was mouseclick in it during last second"?

thanks,
mar.

---

### Post by TheFu on 2015-07-21
focus policy is a window manager thing - WM - not the DE (desktop environment).  Most DEs have a GUI tool to tweak the focus policy or you can modify the WM conf file.  I use openbox .... that file is in ~/.config/openbox/ here.  It is an ugly XML thing. Wish the devs would switch to yaml or stay with old-school text files that humans can actually read.

---

### Post by oldos2er on 2015-07-21
In xfce4 right-click on the desktop, Applications, Settings Manager, Window Manager Tweaks, Focus, click the 'Activate focus stealing prevention' box.

---

### Post by Martin_Mucha on 2015-07-23
There must have been upgrade to this feature; last time I try this it was completely unusable. This time it ± works, except for opening some applications using shortcuts &#8212; weird, but xterm will not get focus, while chrome for instance gets.
Thanks for making me tryhing this feature again, much better now.
M.

---

### Post by Martin_Mucha on 2015-07-23
there's some similar xml (where are the times, when wml were considered superb?) for xfce as well, but there's only ability to turn stealing prevention on, I cannot see there any options how to parameterize it.

---

