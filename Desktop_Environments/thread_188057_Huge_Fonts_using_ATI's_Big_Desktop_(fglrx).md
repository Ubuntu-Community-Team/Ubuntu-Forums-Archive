---
title: "Huge Fonts using ATI's Big Desktop (fglrx)"
date: 2006-06-03
forum: Desktop Environments
---

### Post by wblancqu on 2006-06-03
Take a look at the image in the attachment.
I'm using latest fglrx ATI driver, included in Dapper Drake. aMSN (0.96b from SVN) and Acrobat Reader, also Audacity give me these really ugly fonts, but only when my second monitor is attached. Most applications don't suffer from this "explode my fonts disease :-#". Anyone here having experience with these things, or having the same problem and found a solution?

I've used these commands to setup my xorg.conf:
```

sudo aticonfig --initial=dual-head
sudo aticonfig --tv-format-type=PAL-B --tv-standard-type=SCART --overlay-type=Xv --desktop-setup=horizontal --resolution=0,1280x800,1024x768,800x600 --mode2=1024x768,800x600,640x480 --screen-layout=right
```

Any help would be really appreciated, having these troubles for months now.

---

### Post by Rackerz on 2006-06-03
I don't mean to hi-jack your thread, but how did you install aMSN 0.96b? I can't find anything on it.

---

### Post by wblancqu on 2006-06-03
I've altered the easyAmsn script from Gandalf. Things are quite different now, aMsn uses SVN now (instead of CVS). It's in the attachment. And probably when you've installed it, the TLS module won't download. You can fix this by altering the file ~/msn/autoupdate.tcl
Search for the line that says
```
set baseurl "something tls1.4.1"
```
Problem occurs because that server isn't hosting that file no longer. I've changed the line to this:
```
set baseurl http://surfnet.dl.sourceforge.net/sourceforge/tls/tls1.4.1"
```
Anyway, if there are more questions about this aMsn, let me know and we can make a new thread for it. But please stay with the subject. I really want this Fonts problem to be solved. It's something with fonts that automatically adjust to my (virtual) screen resolution. Anybody knowing more about this?

---

