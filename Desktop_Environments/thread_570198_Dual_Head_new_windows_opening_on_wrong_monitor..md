---
title: "Dual Head: new windows opening on wrong monitor."
date: 2007-10-07
forum: Desktop Environments
---

### Post by Ralphie on 2007-10-07
Hi all,
I came from windows, after it crashed on me *for the last time!*
The get-going was rough, but now that the drivers I need are all installed and working, things have gotten very smooth.

After being unsuccessful at getting dual heads to work, many times over, this tutorial straightened it all out in less than a minute (for anyone looking to get theirs to work):
[http://www.zulustips.com/2007/04/01/...ors-howto.html](http://www.zulustips.com/2007/04/01/...ors-howto.html)
I have just one problem, with the way nvidia TwinView handles new windows.

I understand that it is somewhat of a feature to set new instances of a window on the opposite monitor, for instance, say i have firefox open, and i click a link that opens a new window, it will place it on the other monitor so that i can easily see both.

or if i have one instance of nautilus open, and i want a new window, it will place it on the other screen.

This is probably good for a lot of people, but i don't always like to have my second monitor on, i just use it when I am doing work that requires it, otherwise i like to just stay on one.

If anyone has a tip on how to either disable this feature, or how to work around it, it would be appreciated.

Thank you

---

### Post by aos101 on 2007-10-08
[This thread](http://ubuntuforums.org/showthread.php?t=242502&highlight=metacity+twinview) and [this bug](http://bugzilla.gnome.org/show_bug.cgi?id=145503) talk about the problem a bit.  It looks like they've finally fixed it upstream, and the linked to bug has a link to a deb which apparently has the fix.

This isn't a feature of Twinview - it's handled by the window manager as far as I know.  I switched back to Kubuntu with the KDE KWin window manager because of this problem (they have some settings which can avoid this problem), but it's nice to see they've finally fixed it for Gnome users.

---

### Post by Ralphie on 2007-10-08
thanks for the help,
I did do a search, but all I could come up with were people talking about how it was a 'feature' :)

Thanks again!

I will be giving this a try as soon as I get home

---

### Post by Ralphie on 2007-10-26
UPDATE
**This problem is solved by running compiz**

---

