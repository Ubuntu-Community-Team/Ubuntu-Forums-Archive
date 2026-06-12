---
title: "how do I logoff someone else?"
date: 2006-07-02
forum: Desktop Environments
---

### Post by waster on 2006-07-02
Without going to the command line and killing the other user's processes, how do I logoff someone else from their desktop session? If there are two sessions of my own, can I logoff the old one from the new session without switching.

This is needed when I've opened a freenx session to a machine where I was logged in already. Many applications do not work at all or nicely when they are already up, including firefox, and its not very nice to go round killing processes by hand.

Any ideas?

---

### Post by tomchuk on 2006-07-02
gnome-session-save --kill is probably what you're looking for, you'll probably have to set DISPLAY eg:
```

DISPLAY=:1 gnome-session-save --kill

```

---

