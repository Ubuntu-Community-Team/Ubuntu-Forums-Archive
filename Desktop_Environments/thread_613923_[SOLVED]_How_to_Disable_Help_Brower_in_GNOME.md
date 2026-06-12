---
title: "[SOLVED] How to Disable Help Brower in GNOME ?"
date: 2007-11-15
forum: Desktop Environments
---

### Post by matthewcraig on 2007-11-15
How do I disable the Help Browser in GNOME? I have already tried changing the Preference->Shortcuts menu to "Launch Help Browser" to Disabled. This does not disable the feature anywhere. My F1 key is right next to my ESC key, so I end up launching the browser often, by accident. I very rarely use the help, so I just want it to go away. Any suggestions? Do you think I found a bug in GNOME?

---

### Post by bingoUV on 2007-11-15
Yes, it does seem like a bug in gnome. As a workaround, do the following
```

sudo mv /usr/bin/yelp /usr/bin/yelp1
sudo echo "echo 1" > /usr/bin/yelp
sudo chmod 755 /usr/bin/yelp

```

---

### Post by matthewcraig on 2007-11-16
Thank you very much!  This workaround solved the issue.

---

### Post by matthewcraig on 2007-12-01
Posted this bug report on the GNOME tracker:
[http://bugzilla.gnome.org/show_bug.cgi?id=500881](http://bugzilla.gnome.org/show_bug.cgi?id=500881)

---

