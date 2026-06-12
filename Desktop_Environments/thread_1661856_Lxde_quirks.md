---
title: "Lxde quirks"
date: 2011-01-07
forum: Desktop Environments
---

### Post by DMcCunney on 2011-01-07
I'm running Ubuntu 10.10 on an old Fujitsu Lifebook p2110.  It's a low-end box, with an 867mhz Transmeta Crusoe CPU, a 40GB UDMA 4 HD, and 256MB or RAM (which the Crusoe grabs 16MB of off the top for code morphing.)

I originally installed Xubuntu, but it was extremely sluggish.  I then installed Ubuntu from the Minimal CD, and added desired packages, which helped a lot.

I normally use XFCE4, but have been playing with other desktop environments, including Lxde.  Lxde looks nice enough and runs well enough, but has a couple of annoying quirks.

Quirk one: Lxde looks in ~/Desktop, and displays what it finds as desktop icons.  On my system, icons are sorted by type, with directory entries preceding application launchers, but there seems to be no order with those.  It's not alphabetical by name, or chronological by date stamp.  (I'd prefer alpha by name.)  There doesn't seem to be an option I can set to control this.  Does anyone know how Lxde decides the order in which is displays desktop entries?

Quirk two: File listings in PCManFM don't seem to use standard ASCII collating sequences. When I sort by name, leading non-alpha chars are ignored, so I'll see things like

> 
Charles Dickens
_Copyrighted
Edgar Wallace
@ePub
when I expect to see 
> 
@ePub
_Copyrighted
Charles Dickens
Edgar Wallace
I normally use XFCE4 as my desktop environment, and things display as expected in Thunar.

Is there a simple fix for this, or will it require a new version of the file manager?  It's actually a show stopper for what I do.

Thanks,
______
**Dennis**

---

