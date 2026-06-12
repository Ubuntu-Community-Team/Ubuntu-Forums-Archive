---
title: "How to switch backgrounds automatically"
date: 2009-12-19
forum: Desktop Environments
---

### Post by mahorrocks on 2009-12-19
I have been looking around and came across a nice idea in Mandriva.

Can Ubuntu have its background switching every hour and if so, how?

Also how do I turn of my touchpad everytime my mouse goes into the laptop??

Thanks 

Mark

(I have Ubuntu 9.10)

---

### Post by hariks0 on 2009-12-19
Install wallpaper-tray. Or try wallpapoz.

---

### Post by kadok0520 on 2009-12-20
> **mahorrocks said:**
> I have been looking around and came across a nice idea in Mandriva.

Can Ubuntu have its background switching every hour and if so, how?

Also how do I turn of my touchpad everytime my mouse goes into the laptop??

Thanks 

Mark

(I have Ubuntu 9.10)

try to see my blog article

[http://kadok0520.pixnet.net/blog/post/25520798](http://kadok0520.pixnet.net/blog/post/25520798)

it written by english and chinese.

---

### Post by mahorrocks on 2009-12-22
Seen that but what about Desktop Drapes, any way of making that startup with the ubuntu?

---

### Post by falconindy on 2009-12-22
A lightweight solution would be to use 'feh' with a cronjob. Select a file at random from a directory by doing something such as:
```
#!/bin/sh
WP="/path/to/wallpapers"
feh --bg-scale "$WP/`ls '$WP' | sort -r | tail -1`"
```
Save it, make it executable, and then set that in your crontab as:
```
30 * * * * /path/to/script.sh > /dev/null
```

---

