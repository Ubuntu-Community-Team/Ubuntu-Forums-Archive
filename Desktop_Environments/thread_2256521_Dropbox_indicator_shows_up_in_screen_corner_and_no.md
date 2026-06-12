---
title: "Dropbox indicator shows up in screen corner and not in unity panel"
date: 2014-12-13
forum: Desktop Environments
---

### Post by Klaster on 2014-12-13
Hey folks,

after rebooting my computer today, my dropbox indicator shows weired behaviour. 

Instead of being a normal icon in the unity panel, it shows up in the top left corner (unfortunately over the (x) for closing windows). Check it out:

[ATTACH=CONFIG]258537[/ATTACH]

I'm running Ubuntu 12.04.5 LTS and Dropbox v3.03. 

The style reminds me of a KDE icon, but I have no clue...
Any ideas what happened here and how to reverse it?

Thanks and cheers,
Jakob

---

### Post by vasa1 on 2014-12-13
> **Klaster said:**
> ...
I'm running Ubuntu 12.04.5 LTS and Dropbox v3.03. 

The style reminds me of a KDE icon, but I have no clue...
Any ideas what happened here and how to reverse it?

Thanks and cheers,
JakobQuite a few Linux users are reporting problems of various kinds with the icon from version 3.0.2 onward. Plus the icon seems to be hard-coded and our theme icons are no longer being used.

---

### Post by Klaster on 2014-12-13
Thanks for your reply. I understood that nobody has found a solution so far? Can I run dropbox without the icon then? Its placement is quite.... unfortunate. ;)

---

### Post by vasa1 on 2014-12-13
> **Klaster said:**
> Thanks for your reply. I understood that nobody has found a solution so far? Can I run dropbox without the icon then? Its placement is quite.... unfortunate. ;)Agreed but I don't know how to do that.

I suggest you ask over at dropbox.com so that they come to know about the issue and possibly push out a fix.

---

### Post by Klaster on 2014-12-13
Actually, I restarted dropbox manually and noe the old indicatoris back in place. I will post it in the (abandoned?!) dropbox-forums in case it reappears.

Thanks!

Won't mark this thread solved until I can verify that the issue doesn't arise again.

---

### Post by vasa1 on 2014-12-13
By the way, it seems that Dropbox now uses the icons located in *~/.dropbox-dist/dropbox-lnx.x86_64-3.0.3/images/hicolor/16x16/status*.

I guess with the next update, things will need to be set again :(

---

### Post by Klaster on 2014-12-14
After booting up my computer this morning, the indicator is back in the corner...

Another weired thing: restarting the daemon gives the same result.

```
sudo dropbox stop
...
sudo dropbox start

```

However, stopping the daemon and starting dropbox via the GUI (Start --> Applications --> Dropbox-Icon) brings it back into the unity panel.

There seems to be a difference in the routines. Anyone with more knowledge about that?

Cheers,
Jakob

---

