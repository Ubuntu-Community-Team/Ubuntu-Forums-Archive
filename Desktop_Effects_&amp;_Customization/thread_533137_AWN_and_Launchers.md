---
title: "AWN and Launchers"
date: 2007-08-23
forum: Desktop Effects &amp; Customization
---

### Post by BDNiner on 2007-08-23
How come whenever i add launchers to the AWN bar they disappear when i restart my computer? This happens on one ubuntu machine but not on the other.

---

### Post by BDNiner on 2007-08-23
nevermind i look at some other posts and i answered my own question.

---

### Post by aeortiz on 2007-12-20
ummm, could you please list the right forum posts to look at? AWN loses my launchers after I restore from a "hibernate". (using kubuntu 7.10)

---

### Post by rainwalker on 2007-12-20
> **aeortiz said:**
> ummm, could you please list the right forum posts to look at? AWN loses my launchers after I restore from a "hibernate". (using kubuntu 7.10)

If you drag-and-drop programs into AWN to create the launchers, they don't stay. You have to open up the AWN preferences window and add the launchers.

---

### Post by bradmurmz on 2008-06-23
The best way to launch wine programs I have found is to create a quick shell script called somthing like "wlauncher" and put it into your /usr/bin directory


```

#!/bin/sh
env WINEPREFIX="/home/user/.wine" wine "$1"

```

Then create a launcher from your awn manager that just runs 'wlauncher "C:\path\to\your\program"' 

You can then select your custom icon. Works great for me!

---

