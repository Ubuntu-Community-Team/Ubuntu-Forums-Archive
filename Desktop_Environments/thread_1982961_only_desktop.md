---
title: "only desktop?"
date: 2012-05-19
forum: Desktop Environments
---

### Post by Xandaros on 2012-05-19
Hey there,
Is it possible to install only the desktop of GNOME?
I don't need anything else, but it is always installing lots of stuff when I try to install it with the package manager.
I don't need panels, no file manager, etc. Just a desktop where I can put some starters.

I also won't need a login screen, as it is going to operate with auto-login.

I'll need windows, though. I don't want to start a whole new X session for each and every window :)

Is this possible? How would I do that?

I hope you can help me there.

Edit: Forgot to mention: I'm using the server edition as base.

---

### Post by 2F4U on 2012-05-19
You don't say which package you installed, but I would guess that the package gnome-core for Gnome2. For Gnome Shell there is a nice tutorial here:

[http://tuxfiction.wordpress.com/2011/04/30/how-to-do-a-minimal-gnome3-desktop/](http://tuxfiction.wordpress.com/2011/04/30/how-to-do-a-minimal-gnome3-desktop/)

---

### Post by LeGasp on 2012-05-19
You can perform a minimal install with one of the ISOs in this link: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
And then install only the packages you want, much like a base Debian install or Arch linux.

---

### Post by Xandaros on 2012-05-19
I've tried it with the gnome-core package. Took ages to install.
Well, it even installed pulseaudio.
While I am going to need sound sooner or later, this should not be part of gnome.

I don't like gnome3, so I am going to stick with a gnome2 install if possible.

It installed lots of packages and I am not going to need most of them. (zenity, for example. But that might be a real dependency. But you know what I mean :D)

But even though it installed all that, gnome itself is not working. GDM was installed, too and runs fine. (I didn't want it, but it works -_-)

If I try to login however, it only says ```
Failed to load session "ubuntu"
```The same thing happens if I do "gnome-session" in a xterm.

As for the minimal install: Thanks, I might think about using that instead. But for now I am happy with the server install. (It doesn't come with a desktop either)

By the way: It doesn't necessarily need to be gnome. Anything works for me, as I want such a minimal installation the difference won't be notable.

(Once again: Just a desktop where I can put some icons. These open some applications in windows. No file explorer, panels or anything else)

But thanks for your efforts so far!

Edit: Changing the session to gnome-classic did the trick. (silly me)
However, gnome-core still installs too much. It installs pulseaudio, gnome-panel, nautilus, ...
I am going to install pulse myself, I don't need gnome-panel and need to get rid of the panels and nautilus is also not needed (If it isn't needed to put icons on your desktop, otherwise I'm going to need it).

It even installed empathy!
How can that possibly be part of the "core" package?

---

