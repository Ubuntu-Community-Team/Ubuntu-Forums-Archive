---
title: "emerald decorator in compiz missing right border"
date: 2011-11-22
forum: Desktop Environments
---

### Post by vangop on 2011-11-22
I've installed compiz onto xfce.
Also installed emerald as decorator.
They are working fine, besides 2 issues:
1. windows are missing right border. The top and bottom border line goes over the edge, so it assumes that the right border should be drawn as well.
[[img]http://www.zimagez.com/miniature/screenshot-11222011-050329pm.png[/img]](http://www.zimagez.com/zimage/screenshot-11222011-050329pm.php)

2. Maximized windows have grey solid color titlebar, without text/buttons. The buttons are there, if you hover you get a hint popup. This only happens on fullscreen titles, and I didn't find settings for in in emerald.
[[img]http://www.zimagez.com/miniature/screenshot-11222011-045955pm.png[/img]](http://www.zimagez.com/zimage/screenshot-11222011-045955pm.php)
Anybody?

---

### Post by hhh on 2011-11-22
That's not even the default Emerald theme (Beryl Red). Did you install a theme or mess with settings in emerald-theme-manager? Try renaming the hidden .emerald folder in your home directory and logout/in (which will create a new .emerald folder). If that fixes it, you can delete the old .emerald folder.

---

### Post by vangop on 2011-11-22
I've just customized the colors.
But I did as you've suggested, and the same result.
[[img]http://www.zimagez.com/miniature/screenshot-11222011-093334pm.php[/img]](http://www.zimagez.com/zimage/screenshot-11222011-093334pm.php)

The only thing is that I'm using old emerald, 0.7.2-0ubuntu6.1  , since it is not in 11.10 repos, and I couldn't find a x64 deb of the new one.
And couldn't compile it as well.

---

### Post by hhh on 2011-11-22
Good timing, I just logged back in. :)

The age of Emerald is probably your problem. I use it successfully on a Debian squeeze Xfce setup but haven't tried it with anything more recent than that. Let me boot into that partition and see what version I use...

-edit- 0.7.2-0ubuntu4

You might find some joy here...
[http://ubuntuforums.org/showthread.php?t=1870792](http://ubuntuforums.org/showthread.php?t=1870792)

For help compiling, maybe here...
[http://demonic.cc/?p=50](http://demonic.cc/?p=50)

---

### Post by vangop on 2011-11-22
Thanks for your help.
I've found the new x64 debs [here]("https://launchpad.net/ubuntu/+source/emerald/0.8.8-0ubuntu1/+build/2545502"), and both issues are gone :)
BTW currently emerald won't compile, don't know if that's related with compiz bugs or smth else.
I get
```
main.c:508:8: error: too few arguments to function ‘decor_quads_to_property’
```
And there seems to be some reports of this, without solutions...
I wonder why it's not in the repos anymore.

---

### Post by hhh on 2011-11-22
Np. Great research on that deb! Did you find 32 bit too?

> **vangop said:**
> I wonder why it's not in the repos anymore.
For one thing, from what I've read, the actual Emerald project has been only spottily maintained, and it's supposed to eventually be replaced (maybe by Jasper). As for Ubuntu's input, maybe it's been neglected since they've been doing a ton of work with Unity and Gnome 3.

Maybe mark the OP solved (under thread tools)?

---

### Post by typhoon_tip on 2011-11-22
**0.9.4** works very well on Ubuntu 11.10 and *Unity* too ! Believe it or not :popcorn:

I suggest you compile 0.9.4 and install it manually (0.9.5 is the latest version, but it doesn't compile as it require newest compiz from GIT to be compiled manually as well).

A few glitches remain tough, as I stated in the thread. Maximized windows still loose the buttons (strange, it never happened on my 10.04 LTS and 10.10 installs).

Have a look at here:
[http://ubuntuforums.org/showthread.php?t=1870792](http://ubuntuforums.org/showthread.php?t=1870792)

---

### Post by vangop on 2011-11-23
> **hhh said:**
> Np. Great research on that deb! Did you find 32 bit too?
Yep, here[here]("https://launchpad.net/ubuntu/+source/emerald/0.8.8-0ubuntu1") is the src package, it has links to diff architectures.


> A few glitches remain tough, as I stated in the thread. Maximized windows still loose the buttons (strange, it never happened on my 10.04 LTS and 10.10 installs).

Why do you bother with it then? Does it offer smth over 0.8.8 version?
Since the latter runs smoothly, I didn't notice any issues. From what I see in emerald's git the latest commits are for 0.8.8..

---

### Post by typhoon_tip on 2011-11-23
> **vangop said:**
> Why do you bother with it then? Does it offer smth over 0.8.8 version?
Since the latter runs smoothly, I didn't notice any issues. From what I see in emerald's git the latest commits are for 0.8.8..

Nothing indeed, I have tested out 0.8.8 and works exactly the same as 0.9.4.

Does anyone has the same issue when maximize/restore windows, that titlebar's icons (close, minimize, maximize etc.) go missing ? Resizing the window bring them back.

---

