---
title: "Index corrupted"
date: 2009-06-04
forum: General Help
---

### Post by jhouse59 on 2009-06-04
I'm using Ubuntu 9.04. The last couple of days. I'm getting a pop-up box. That says : "Tracker There was an error while performing indexing: Index corrupted". When I click on the "Reindex all contents". Nothing happens. A box shows up that says: "Re-index your system? Indexing can take a long time. Are you sure you want to re-index?". I'll click yes. But, the Tracker box still stays on my desktop.
What could be causing this? How can I fix it?

---

### Post by Soul-Sing on 2009-06-04
```
sudo apt-get install tracker-utils
tracker-processes -r # --hard-reset
```

---

### Post by CaptainMark on 2009-06-04
This was a known bug on realease of 9.04, I thought they were going to release an update for this, never mind the work around is easy enough

---

### Post by jhouse59 on 2009-06-07
Thanks for the replies. I never got an email saying someone had replied to this. So I just did a re-install.

---

