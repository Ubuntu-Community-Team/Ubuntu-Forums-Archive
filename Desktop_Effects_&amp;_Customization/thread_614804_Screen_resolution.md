---
title: "Screen resolution"
date: 2007-11-16
forum: Desktop Effects &amp; Customization
---

### Post by laptop69 on 2007-11-16
Under Windows XP and Mepis my screen is set to or can be set to 1024 x 768 but under Ubuntu I can only use 800 x 600. can I force Ubuntu to let me use 1024 x 768?

All help greatfully received.

---

### Post by PatrickFisher on 2007-11-16
It is possible to do. However, a disclaimer first.

You should back up all the files you change (should only be xorg.conf). If this gets screwed up, you may not be able to boot into X, so make sure you know how to replace your updated/broken file with the backup.

Now, onto the fun part. Run:
```

sudo gedit /etc/X11/xorg.conf

```

Change the resolution found in the file, and restart. Hopefully this works. If you can't boot into X, just revert and you'll be back to "normal".

---

