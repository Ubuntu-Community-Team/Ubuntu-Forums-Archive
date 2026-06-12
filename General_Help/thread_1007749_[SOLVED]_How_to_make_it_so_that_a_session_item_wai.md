---
title: "[SOLVED] How to make it so that a session item waits a minute before it starts?"
date: 2008-12-10
forum: General Help
---

### Post by josephellengar on 2008-12-10
My gmail-notify always starts up before the internet connects, and gives me a warning.  So, how do I make it wait for a while so that the internet will have time to start before it starts?  Thanks!

---

### Post by sdennie on 2008-12-10
Try changing the session command to:

```

sh -c "sleep 60 && gmail-notify"

```

Where 60 is 60 seconds.  You could get more fancy with this and make it wait for a network connection to appear but, this should do what you want.

---

