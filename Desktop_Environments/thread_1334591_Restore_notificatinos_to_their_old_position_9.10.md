---
title: "Restore notificatinos to their old position 9.10"
date: 2009-11-22
forum: Desktop Environments
---

### Post by josephellengar on 2009-11-22
So, I finally got with the program and moved from good, old, stable Ibex to Karmic.  I've got just one gripe.  The notifications are about an inch below my top bar, which is really annoying.  Is there any way to put them in the same position as in Jaunty?

Also, a few other questions:

1) Where do I go to install the new software center and Ubuntu One that I've been hearing about?

2) Is it no longer possible to change the login screen theme?

3) In Ibex I could make conky semi-transparent through compiz.  Is that no longer possible?  Thank you!

---

### Post by VCoolio on 2009-11-22
the notification position is ok, there has been a debate on it; this is what the ubuntu devs want. If you, like me, want the old position, add these repos and install osd from there:

deb [http://ppa.launchpad.net/gilir/updates/ubuntu](http://ppa.launchpad.net/gilir/updates/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/gilir/updates/ubuntu](http://ppa.launchpad.net/gilir/updates/ubuntu) karmic main

To make conky transparent: why not use conky features? In your conkyrc make sure you have these:

own_window yes
own_window_type normal # or desktop, override, dock
own_window_hints sticky,skip_pager,undecorated,skip_taskbar,below
own_window_transparent yes

EDIT: realized this is not semitransparant. Check out the new lua possibilities for a semitransparant background here: [http://conky.linux-hardcore.com/?page_id=3002](http://conky.linux-hardcore.com/?page_id=3002)

---

### Post by josephellengar on 2009-11-22
> **VCoolio said:**
> the notification position is ok, there has been a debate on it; this is what the ubuntu devs want. If you, like me, want the old position, add these repos and install osd from there:

deb [http://ppa.launchpad.net/gilir/updates/ubuntu](http://ppa.launchpad.net/gilir/updates/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/gilir/updates/ubuntu](http://ppa.launchpad.net/gilir/updates/ubuntu) karmic main

To make conky transparent: why not use conky features? In your conkyrc make sure you have these:

own_window yes
own_window_type normal # or desktop, override, dock
own_window_hints sticky,skip_pager,undecorated,skip_taskbar,below
own_window_transparent yes

EDIT: realized this is not semitransparant. Check out the new lua possibilities for a semitransparant background here: [http://conky.linux-hardcore.com/?page_id=3002](http://conky.linux-hardcore.com/?page_id=3002)

Thank you.  I figured it out.  For some reason my conkys weren't transparent because compiz wasn't starting automatically on startup anymore (weird).  Would you have any idea how I could get my flash to work though?  I'm really desperate to get that to work to do some homework that I need to do and the koala broke it, even when I install directly from the adobe site.

---

### Post by VCoolio on 2009-11-23
only flash thing I do is install flashplugin-nonfree. Better post a new thread because the flash gurus won't read this one about nofitications. Also a little searching on these forums or google may already help; there are a lot of flash issues (adobes fault if you ask me, not ubuntu's), or ask in irc #ubuntu.

---

