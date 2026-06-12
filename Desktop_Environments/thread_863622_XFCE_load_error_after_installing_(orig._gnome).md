---
title: "XFCE load error after installing (orig. gnome)"
date: 2008-07-18
forum: Desktop Environments
---

### Post by spaceboy909 on 2008-07-18
I've been using Gnome (Hardy), and wanted to install xfce to save resources.

First I tried via synaptec, and installed the main package.  This yielded an incomplete desktop and an error message.

I looked online and found instructions to use apt.  It seemed to install fine, but I'm getting the same error message and still getting an incomplete desktop.

It's incomplete in that I have no taskbar, and possibly more missing that I haven't seen yet.

The error message is (paraphrased): ```
....cannot find internet address for 'your-desktop'......As a result, XFCE will not operate correctly.  You may be able to fix this problem by adding 'your-desktop' to /etc/hosts file.
```

I've decided not to tinker with this until I get some help, as I don't want to lose anything.

---

### Post by ibutho on 2008-07-18
Add a line like the one below to your /etc/hosts file.
```
127.0.1.1	your-desktop
```

---

### Post by spaceboy909 on 2008-07-18
Thanks, that cleared up the error message, at least.  Looking at my hosts file, there was an extension (my name) that had been added to the end of the host name:  my-desktop.MARK.

I commented that out, and added the normal one.

But, I still have the missing taskbar issue.  Apparently, it's called a 'panel' in Xubuntu?  Well, by default, it's showing a one button, small floating panel which has no default functionality.

xfce4-panel is running.

Any help is appreciated.

---

### Post by spaceboy909 on 2008-07-18
Ok, I've at least found a work around for now.  Hopefully it's just a one time glitch, but it doesn't sound like it bassed on other threads I've found.

My solution:  1) **xfce4-panel -x**, 2) **xfce4-panel &**.  For reference, here are the links I found:

[https://bugs.launchpad.net/xfce4-panel/+bug/53897](https://bugs.launchpad.net/xfce4-panel/+bug/53897)
[https://bugs.launchpad.net/ubuntu/+source/xfce4-panel/+bug/138902](https://bugs.launchpad.net/ubuntu/+source/xfce4-panel/+bug/138902)
[http://bugzilla.xfce.org/show_bug.cgi?id=2130](http://bugzilla.xfce.org/show_bug.cgi?id=2130)
[http://ubuntuforums.org/showthread.php?p=1769745](http://ubuntuforums.org/showthread.php?p=1769745)

---

