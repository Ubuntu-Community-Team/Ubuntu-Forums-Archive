---
title: "Startup Manager Problems in XFCE"
date: 2009-04-29
forum: Desktop Environments
---

### Post by Peteo on 2009-04-29
Hey folks,

I'm having a problem with the session startup manager in XFCE (running on Ubuntu 9.04):

On startup a whole bunch of programs (pigeon, conky, etc.) start up automatically. I went into the startup manager and removed the programs (pigeon was never even listed there) from the startup manager, however, they're still starting up with every new session.

In addition, when I do "ps ux" in the terminal it displays that I am starting up with three separate instances of conky with every session!

I don't have "save session for future logins" or anything like that enabled so I'm kind of at wits end. Does anyone have any thoughts on what might be causing this issue?

(Oh, and this is within my first week of ever having used linux so understand I don't know all the tricks yet :()

Thanks.

---

### Post by kanikilu on 2009-04-29
I'm kind of new to XFCE myself, but try this: close any programs that you **don't** want to run at startup, then when you log out, **check** the Save Session box.

If that doesn't work, another option, which I want to say I used successfully a few weeks ago, is to manually remove any saved sessions.

To do this, I think you just need to remove (or in this example, move) the sessions directory in the cache.  Go to a terminal a try the following:
```
mv ~/.cache/sessions ~/.cache/sessions-backup
```
Then log out (without saving the session) and log back on...

---

