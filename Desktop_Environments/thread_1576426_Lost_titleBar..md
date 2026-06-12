---
title: "Lost titleBar."
date: 2010-09-17
forum: Desktop Environments
---

### Post by finito on 2010-09-17
I was screwing around with KDElibs5, because of the following errors during install of any KDE app

```
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

```

After reading around I found out this is not a Ubuntu bug but a KDE bug, so I unistalled kdelibs5 with 'apt-get remove kdelibs5'

This in turn got rid off all my kde apps.

So I reinstalled Amarok with apt-get install.

well It didn't help the thing still wouldn't work, so I read some other posts and got amarok to work. So I thought lets restart because my sound applet disappeared and I lost the panel applet.

after the restart I noticed that my title bar was missing and my panel was screwy.

I thought at least amarok works now. Guess what it doesn't.

So now I am thinking of a clean install or is there a way to fix this.

---

### Post by scorchgeek on 2010-09-17
I don't know much about this, but I might suggest reinstalling/reconfiguring GNOME--that said, that might be nearly as much work as a fresh install.

---

### Post by TwelveGauge on 2010-09-17
what it looks like to me is one of those compiz things SO if you run compiz:

System -> Prefs -> advanced desktop effects -> window decoration -> enable.

---

