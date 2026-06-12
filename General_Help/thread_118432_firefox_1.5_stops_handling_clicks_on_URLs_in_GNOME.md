---
title: "firefox 1.5 stops handling clicks on URLs in GNOME"
date: 2006-01-17
forum: General Help
---

### Post by dguido on 2006-01-17
I installed firefox 1.5 with the guide in the wiki ([https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)) and now when I click on links I dragged to my desktop or links in gaim IM conversations firefox fails to open.  Did I forget to make a symbolic link somewhere?

---

### Post by quonsar on 2006-01-17
this will fix you up:

```
sudo ln -s /opt/firefox/firefox-bin /opt/firefox/mozilla-firefox-bin
```

---

### Post by nanotube on 2006-01-17
or go to system > preferences > preferred applications, and point the web browser one to your firefox1.5 binary. methinks this should clear it up.

---

### Post by dguido on 2006-01-19
Thanks!  Looking in preferred apps made me try to run mozilla-firefox in a terminal.  It gave me an error stating that the launcher script couldn't find /opt/firefox/mozilla-firefox.  When I checked I found out that didn't /opt/firefox/mozilla-firefox exist which made me realize the mozilla-firefox script in /usr/bin was left over from 1.0.7.  So I deleted it and made a symbolic link to the new one:
```
sudo rm /usr/bin/mozilla-firefox
sudo ln -s /usr/bin/firefox /usr/bin/mozilla-firefox
```
all better!

UPDATE: Uhhhh actually that didn't work... I just deleted mozilla-firefox and changed preferred apps to point to firefox.

---

