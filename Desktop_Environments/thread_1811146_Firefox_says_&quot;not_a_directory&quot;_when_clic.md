---
title: "Firefox says &quot;not a directory&quot; when clicking on downloaded file"
date: 2011-07-24
forum: Desktop Environments
---

### Post by antekone on 2011-07-24
Hi. I've upgraded Maverick to Natty, and since then I'm having one problem with Firefox.

I have a list of downloaded files in FF. Clicking on every file (pdf, png, iso, etc) gives me an error, like: "Can't open <filename>: This location is not a directory". The error message is the same as if I'd run **nautilus <filename>**, and in fact it seems to originate from nautilus. Also FF seems to ignore my settings under Preferences -> Applications, where I can choose what program to use for different file types. Does anyone know the solution for this?

---

### Post by antekone on 2011-07-25
I've tried removing .mozilla folder in my ~. Firefox had default settings again, but problem persisted.

---

### Post by nerdy_kid on 2011-07-25
scan your filesystem for errors by doing:

```

sudo touch /forcefsck

```

and reboot.  See if the problem persists then.

---

### Post by eggeral on 2011-07-25
Try removing the "exo-utils".

sudo apt-get remove exo-utils

This also removes thunar but worked for me.

---

### Post by antekone on 2011-07-26
Removal of exo-utils helped, thanks!

The problem is that with removing exo-utils, apt wants also to delete xfce4-terminal, which I use instead of gnome-terminal. But now I have a hint where to look for the real problem. Thanks again ;]

---

