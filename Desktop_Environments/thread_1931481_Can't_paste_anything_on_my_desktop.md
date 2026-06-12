---
title: "Can't paste anything on my desktop"
date: 2012-02-25
forum: Desktop Environments
---

### Post by Luz77 on 2012-02-25
I know [this topic]("http://ubuntuforums.org/showthread.php?t=1039167") is 3 years old, but I got exactly the same problem. I can't paste on the desktop.

> **mali2297 said:**
> Go to *Settings Manager* and then *Desktop*. Check that the option *Allow Xfce to manage the desktop* is enabled.
I can't find that option... Maybe this option is not available anymore?

---

### Post by Iowan on 2012-02-25
New thread created:
> If a post is older than a year or so and hasn't had a new reply in that time, [COLOR="Red"]instead of replying to it, create a new thread[/COLOR]. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. [COLOR="Red"]You may link to the original discussion in the new thread if you think it may be helpful.[/COLOR]

---

### Post by musicman10489 on 2012-02-29
You can access this through **Advanced Settings** -> **Desktop** -> **Have file manager handle the desktop**.

If you do not have **Advanced Settings** installed, open your terminal and type
```
$ sudo apt-get install gnome-tweak-tool
```

Good luck :)

---

### Post by LewisTM on 2012-02-29
In the current state of things you cannot paste on the Xfce desktop. That's one resilient bug. You have to drag and drop or use the Send To/Desktop (Create Link) context menu.
I've looked at 12.04 alpha2 and the bug is finally fixed!

Big cheers! ;)

---

