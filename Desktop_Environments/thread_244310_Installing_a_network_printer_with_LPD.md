---
title: "Installing a network printer with LPD"
date: 2006-08-26
forum: Desktop Environments
---

### Post by jnoreiko on 2006-08-26
I have a not-very-new print server which (AFAIK) won't work with CUPS, but does support LPD.

The printer appears to be recognized, and when I print a test page, the status in the printer's Properties window says
```
Printing: Spooling LPR job, 0% complete...
```

However, it doesn't get any further than that. :(

I've managed to get it to work with OS X, using LPD, so in theory it should also work on Ubuntu... however, practice is not the same as theory ;)

I have the following setting in the printer Properties window in the Connection tab:

Host: 192.168.0.6
Queue: /192.168.0.6//lpt1

This isn't the same presentation as on the CUPS webserver on OS X -- in that, it's split into location "lpt://192.168.0.6" and queue "lpt1", but when I put it in like that it rearranged itself into the above.

I've looked at the local CUPS webserver, and it seems the URI is getting mangled. It says:
```
Device URI: lpd://192.168.0.6//192.168.0.6//lpt1
```

Unfortunately, I can't fix this through CUPS as it requires a password (and neither mine nor root's login works).

---

### Post by jnoreiko on 2006-08-26
Got it to work!

I went via CUPS and fixed the bad URI.
Filed this: [http://bugzilla.gnome.org/show_bug.cgi?id=352974](http://bugzilla.gnome.org/show_bug.cgi?id=352974)

(I'm not sure it's in the right component though.)

---

