---
title: "Cannot log into X session"
date: 2010-06-21
forum: Desktop Environments
---

### Post by Mooseknuckle on 2010-06-21
Hello  after an update yesterday, I cannot log into my X session ...

The first time I tried, my screen showed a KDE background, and I got the error:

could not start ksmserver check your installation

then I had to click ok, and it put me back to the log in screen.

I opened a shell (ctrl-alt-F1), logged in and typed:

sudo apt-get remove ksmserver, and it told me there was nothing to remove, but said I had a bunch of stale packages and to apt-get autoremove them, and I did

Now, when I go to the log in screen (X), under sessions, it only has xterm (no gnome, no kde) ...

[edit]

I forgot to add, I have always used Gnome, and not kde ... I have no idea why it originally tried to throw me into a KDE session

How can I get my gnome desktop environment back so I can log in again?   I have no idea what I did, nor how to get back to normalcy!  

Thanks for ANY help!

---

### Post by Tylerjd on 2010-06-22
I would first try to start x by logging into the xterm session and putting the command in: ```
startx
```

Beyond that I really can't help you at this moment as I'm answering these by iPhone. But I will look into it.

EDIT: also, if x doesn't start, first, try  sudo startx  then, check to make sure you have gnome installed. I have never had to login to xterm so idk what you can do.

---

