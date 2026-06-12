---
title: "firefox next/previous buttons not working"
date: 2009-02-20
forum: General Help
---

### Post by miroslav_karpis on 2009-02-20
Hi All,

after reinstalling of firefox (automatic update) the left up buttons are desabled - previous/next page. Strange no?

Pls. does anybody know why?

Thnks.

---

### Post by geirha on 2009-02-20
Have you restarted firefox after the update? Firefox behaves weird if its files get changed while it is running.

---

### Post by miroslav_karpis on 2009-02-20
yes...many times, firefox, pc.... (restarted)...nothing...

---

### Post by geirha on 2009-02-20
Close firefox, then open a terminal and type: ```
firefox -ProfileManager
``` 
ProfileManager must be written with capital P and capital M (case sensitive).

You should get firefox' profile manager, where you'll see just one profile called default. Create a new profile, and start firefox with that profile. Do you get the same behavior while running with the new profile?

---

### Post by miroslav_karpis on 2009-02-20
thnks....that helped...(now just to solve 3 other ubuntu-issues) and will be a happy ubuntuoid ;)

---

