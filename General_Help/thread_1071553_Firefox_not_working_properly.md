---
title: "Firefox not working properly"
date: 2009-02-16
forum: General Help
---

### Post by estanton on 2009-02-16
Firefox 3 has stopped functioning properly for me all of a sudden. I ran an update yesterday, and later that day I noticed that the back button in the browser is no longer functioning. I've also lost all my bookmarks. Any ideas on how to solve this problem or correctly reinstall firefox?

---

### Post by kanikilu on 2009-02-16
I actually had this happen to me a couple weeks ago. I have no idea what caused it, but I believe I fixed it by just creating a new profile. I didn't delete the old one, I just renamed it and then let Firefox create a new one.

To do that, go to /home/yourUserName/.mozilla/firefox and rename the default profile directory ([randomString].default) to something else (I just changed the .default part to .default-backup).

---

### Post by estanton on 2009-02-16
firefox isn't creating a new one :( it just gets stuck and says it's already running.
I tried pulling up the profile manager from the terminal but the command just pulls up the browser rather than the manager.

---

### Post by estanton on 2009-02-16
Resolved, I changed the name of the old profile then opened up the profile manager. Thanks for the help!

---

