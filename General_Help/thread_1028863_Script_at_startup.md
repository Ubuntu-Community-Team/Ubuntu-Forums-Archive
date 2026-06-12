---
title: "Script at startup"
date: 2009-01-02
forum: General Help
---

### Post by duiu on 2009-01-02
I need to execute a script at startup. I set up init.d to do this, however the script outputs stuff to the screen and isn't a daemon, and thus screws everything else up because it takes up the output and doesn't stop, so everything gets stuck. How do I make it just run in the background?

The script is a script that starts a UPnP server so I can stream to my Xbox 360.

---

### Post by DGortze380 on 2009-01-02
> **duiu said:**
> I need to execute a script at startup. I set up init.d to do this, however the script outputs stuff to the screen and isn't a daemon, and thus screws everything else up because it takes up the output and doesn't stop, so everything gets stuck. How do I make it just run in the background?

The script is a script that starts a UPnP server so I can stream to my Xbox 360.

Put an ampersand after it.

myScript &

---

