---
title: "Thunderbird Opens Links in Konqueror Instead of Firefox"
date: 2006-09-28
forum: Desktop Environments
---

### Post by srunni on 2006-09-28
Well, I guess the title says it all....when I click on a link in Thunderbird, it opens a Konqueror window, instead of opening it in Firefox. Everything else, even the KDE applications, open links in Firefox, and Firefox is set as the default browser.

Any ideas?

Thanks in advance for the help

---

### Post by mitch.c on 2006-09-29
> **srunni said:**
> Well, I guess the title says it all....when I click on a link in Thunderbird, it opens a Konqueror window, instead of opening it in Firefox. Everything else, even the KDE applications, open links in Firefox, and Firefox is set as the default browser.

Any ideas?

Thanks in advance for the help
Add the following lines to user.js in your Thunderbird profile:
```
user_pref("network.protocol-handler.app.http", "/usr/bin/firefox");
user_pref("network.protocol-handler.app.https", "/usr/bin/firefox");
user_pref("network.protocol-handler.app.ftp", "/usr/bin/firefox");

```

If you don't have a user.js, just create one. Path to your profile is ~/.mozilla-thunderbird/somelongstringofrandomcharacters/

---

### Post by aysiu on 2006-09-29
Read [this](http://ubuntuforums.org/showthread.php?t=60427).

---

### Post by srunni on 2006-09-29
Thanks for the help. I just added what mitch.c said to prefs.js, like the thread aysiu linked to said. It's working great now!

---

