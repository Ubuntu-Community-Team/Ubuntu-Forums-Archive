---
title: "Firefox"
date: 2005-05-03
forum: Desktop Environments
---

### Post by rum beverage on 2005-05-03
When I try to set my preferred applications in firefox, for example azureus with .torrent files.  It does not save these settings.  I don't even have access to the File Types window unless I run firefox with sudo.  I'm just wondering how I can fix this.

---

### Post by cdhotfire on 2005-05-03
try

```

$ sudo chown username:username ~/.mozilla
$ sudo chown username:username ~/.mozilla/*

```

username is your username.:)

---

### Post by rum beverage on 2005-05-04
[QUOTE=cdhotfire]try

```

$ sudo chown username:username ~/.mozilla
$ sudo chown username:username ~/.mozilla/*

```

username is your username.:)[/QUOTE]
 The ownership of all the files and subdirectories was already my user (and I ran 'sudo chown -R username:username ~/.mozilla/*' as a precaution).  There's no rhyme or reason I can think of apart from it using files in /usr/lib/mozilla-firefox

---

### Post by rum beverage on 2005-05-10
bump?

---

### Post by cdhotfire on 2005-05-17
it stores your profile stuff under your homefolder.  Saved settings go under here, so that has nothing to do with /usr/lib/mozilla-firefox wish is under root command.  So it must not be saving your files under /home/username/.mozilla/firefox (sometin like this, not on ubuntu at the moment) and check the write preferences on the things here.  If its something else, then i have no ideo.:-\"

---

