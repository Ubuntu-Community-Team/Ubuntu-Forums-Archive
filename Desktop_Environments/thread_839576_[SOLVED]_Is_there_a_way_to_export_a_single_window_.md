---
title: "[SOLVED] Is there a way to export a single window in the X display?"
date: 2008-06-24
forum: Desktop Environments
---

### Post by Ironchew on 2008-06-24
I'm not certain if this is an X server question or a window manager question (or both).  I know how to export the entire X display to another computer, but I think it would reduce bandwidth consumption, processing power, and latency to export a single window instead of the entire display.  Is there a way to do this?  Thanks for the feedback.

---

### Post by pytheas22 on 2008-06-24
You can export single windows over ssh.  Install an ssh server on the host machine (apt-get install ssh should do it) and on the client machine, connect with:
```

ssh username@ipaddress-of-host -X
```

then you should be able to forward individual applications; e.g. if you type "firefox," you'll get just a window for Firefox.  Keep in mind that if the client machine runs OS X or Windows, you need to install X windows first for this work.  Also depending on the speed of your network connection, X11 forwarding over ssh can be pretty slow for big applications, but maybe it will be acceptable for you.

I think you can also forward individual applications over vnc, but I don't know how.

---

### Post by Ironchew on 2008-06-24
To pytheas22:
Exactly what I was looking for.  Thanks for replying so quickly.

---

### Post by pytheas22 on 2008-06-24
No problem, and thanks for thanks.  And I made a typo; the correct command should be:
```

ssh -X username@ipaddress-of-host
```

(the -X should go right after ssh or it probably won't work, and the -X is important if you want to forward X11 applications over ssh).

Also I should have mentioned that there can be some problems that you'll run into trying to forward X11, but if you google the error messages, you should be able to work past them.  Or come back here if not.

---

