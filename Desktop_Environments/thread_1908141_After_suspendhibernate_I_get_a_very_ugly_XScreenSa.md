---
title: "After suspend/hibernate I get a very ugly XScreenSaver login window"
date: 2012-01-12
forum: Desktop Environments
---

### Post by maulynvia on 2012-01-12
Lubuntu Rocks - its fast and good looking.

One thing spoils the overall impression. After a suspend or hibernate. When restarting I get this very ugly XScreenSaver 5.14 login window that spoils the overall impression.

Is there a way to replace this with something more elegant?

Maul

---

### Post by maulynvia on 2012-01-16
To answer my own question....

The answer appears to be "No, the ugly login after hibernate cannot (easily) be replaced."

The windowing toolkit is not used for the login window after suspend/hibernate as this might compromise security. Unlike other situations (demos and startup), when suspended or hibernated, a user has already been authenticated and there must be no possibility of a bug in the screen saver or windowing toolkit enabling a user to bypass the login window, See [http://www.jwz.org/xscreensaver/faq.html#toolkits](http://www.jwz.org/xscreensaver/faq.html#toolkits).

Having understood this, it makes perfect sense to prioritise security over cosmetics.

---

