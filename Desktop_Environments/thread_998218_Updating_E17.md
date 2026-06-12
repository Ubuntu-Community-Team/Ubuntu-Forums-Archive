---
title: "Updating E17"
date: 2008-11-30
forum: Desktop Environments
---

### Post by toasty_ghosty on 2008-11-30
Hello

I've been using Enlightenment for awhile. Installed it with this:

> [http://ubuntuforums.org/showthread.php?t=546746](http://ubuntuforums.org/showthread.php?t=546746)

I'm doing this:

> sudo easy_e17.sh -u

I'm upgrading via the script. It mentions upgrading on that page, but I cannot seem to do this correctly. When it starts upgrading (before installation) it says almost every package is broken. I do not know why this is. I cannot imagine that all packages would be broken.

Thanks for the help.

---

### Post by Tux Aubrey on 2008-11-30
Have you updated the script?( via the methods in this post: [http://ubuntuforums.org/showthread.php?t=916690](http://ubuntuforums.org/showthread.php?t=916690))

Depending on how long it has been since you installed e17 via easy_e17, the changes to both e17 and the script may have been quite substantial (accelerating over the past two weeks too). 

Rui's update scripts now handle a lot more error checking too, so, if you can't get an update, it may even be worth reinstalling the lot.

---

### Post by toasty_ghosty on 2008-11-30
Thanks for the help Again Tux

The part I am confused with is when it tells me there is a conflict and it wants me to postpone, diff-full(Have no idea what that is) or edit.

Hopefully you can enlighten me......sorry about the horrible pun.

---

### Post by Tux Aubrey on 2008-12-01
> **toasty_ghosty said:**
> Thanks for the help Again Tux

The part I am confused with is when it tells me there is a conflict and it wants me to postpone, diff-full(Have no idea what that is) or edit.

Hopefully you can enlighten me......sorry about the horrible pun.

I'm not sure if its the same problem that some people were having with some broken *.po files.  According to The Man (Rui), the solution was to hit "r" when that question comes up.  I haven't hit this problem, so I don't even know what all the options are (or mean).

---

### Post by worldwithoutgurus on 2008-12-01
If you're using E17 svn, just type tf when that question comes up.

---

