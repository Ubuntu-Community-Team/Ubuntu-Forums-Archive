---
title: "Firefox - how to set home page on terminal?"
date: 2006-10-04
forum: Desktop Environments
---

### Post by bazzer on 2006-10-04
Hi
Is there a way I can configure Firefox from the terminal? I'm installing a certain way, and I need to set the browser home page for ALL users of the system.

I've found the prefs.js file but it doesn't casecade down to the user profiles as they are created, some of the lines are copied and some aren't.
Anyone done this before?

---

### Post by aysiu on 2006-10-04
Ask [mhancoc7](http://ubuntuforums.org/member.php?u=7727), who created a custom Ubuntu for Christians and customized the Firefox homepage.

---

### Post by bazzer on 2006-10-12
Ok, I've managed to sort this one after trial and error. For anyone who is interested:

You need to edit /etc/firefox/profile/prefs.js to include a line like:

user_pref("browser.startup.homepage", "http://www.ubuntuforums.com/");

Any Firefox profiles created subsequently will inherit these settings.
:)

---

