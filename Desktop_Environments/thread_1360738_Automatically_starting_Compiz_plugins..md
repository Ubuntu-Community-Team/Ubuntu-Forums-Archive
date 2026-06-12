---
title: "Automatically starting Compiz plugins."
date: 2009-12-21
forum: Desktop Environments
---

### Post by marshall.robert on 2009-12-21
Hi,
I was wondering if it is possible to start Compiz plugins, that have no "auto-start" feature, automatically at login, for example. Being able to start them on specific times and dates would be a real bonus.

I am mainly thinking about the Snow plugin, but I am hoping it could be expanded to others in the future.

I thought that this could probably be achieved with a script, but I know nothing about Linux scripts.

Thanks,
Rob.

---

### Post by marshall.robert on 2009-12-22
Bump

---

### Post by dougrussell081869 on 2010-01-10
Well, this is an old post, but I was wondering the same thing and google didn't turn up any answers so I came up with a solution myself.  First off, I am running Gentoo with XFCE, but I doubt it matters.  I had the compiz DBUS plugin enabled and I created the following script, which I called toggle-snow...

```

#!/bin/bash
sleep 2
dbus-send --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/snow/allscreens/toggle_key org.freedesktop.compiz.activate string:'root' int32:`xwininfo -root | grep id: | awk '{ print $4 }'`

```

Then I just have this script execute at login.  Maybe there is a more elegant solution, but this worked for me.

---

