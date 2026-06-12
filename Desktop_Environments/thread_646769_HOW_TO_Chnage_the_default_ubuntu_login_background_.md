---
title: "HOW TO: Chnage the default ubuntu login background color."
date: 2007-12-21
forum: Desktop Environments
---

### Post by inoxllor on 2007-12-21
**Tested on Ubuntu 7.10**

Use Terminal and run this:
**sudo gedit /etc/gdm/PreSession/Default**

Then Find the Line that says:
> if [ "x$BACKCOLOR" = "x" ]; then
BACKCOLOR="#dab082"

And change it to:
> if [ "x$BACKCOLOR" = "x" ]; then
BACKCOLOR="#000000"

Note that #000000 is pure black. 
You can use your favorite color.
Check this site:
[http://cloford.com/resources/colours/500col.htm](http://cloford.com/resources/colours/500col.htm)

:)

---

### Post by K.Mandla on 2007-12-25
Moved to Desktop Environments.

---

### Post by phyrewall on 2007-12-25
> **inoxllor said:**
> **Tested on Ubuntu 7.10**

Use Terminal and run this:
**sudo gedit /etc/gdm/PreSession/Default**

Then Find the Line that says:


And change it to:


Note that #000000 is pure black. 
You can use your favorite color.
Check this site:
[http://cloford.com/resources/colours/500col.htm](http://cloford.com/resources/colours/500col.htm)

:)

Thanks for this, it's been bothering me for months. :guitar:

---

