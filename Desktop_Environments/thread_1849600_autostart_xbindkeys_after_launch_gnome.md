---
title: "autostart xbindkeys after launch gnome"
date: 2011-09-24
forum: Desktop Environments
---

### Post by parmaster on 2011-09-24
add to autostart xbindkeys not working ):P
may be a problem in the absence of delays in loading :-s
after 10 hours of hard work, i found the decision on web site of Gentoo Russion Community

code to .profile (home directory):
```
[B]if [ -n "$DISPLAY" ] ; then
if [ -z `pgrep xbindkeys` ] ; then
xbindkeys
fi
fi[/B]
```i get it here:
[http://www.gentoo.ru/content/resheno-kak-zapustit-xbindkeys-pri-zagruzke-sistemy](http://www.gentoo.ru/content/resheno-kak-zapustit-xbindkeys-pri-zagruzke-sistemy)

privet vADIM :popcorn:

---

