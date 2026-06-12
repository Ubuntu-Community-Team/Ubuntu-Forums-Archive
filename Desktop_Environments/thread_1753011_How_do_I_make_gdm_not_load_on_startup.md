---
title: "How do I make gdm not load on startup?"
date: 2011-05-08
forum: Desktop Environments
---

### Post by exabyte on 2011-05-08
I edited some file in /etc and it stopped loading, but after upgrading to natty it loads again. I'm already starting X manually from /etc/event.d/tty7, but the X started from gdm is the one I see on the screen. I don't have a keyboard, so I can't switch to the console with the right X after startup. Is the only option to deinstall gdm, or is there a way to make it not start?

"man stop" says nothing useful.

---

### Post by cipherboy_loc on 2011-05-08
This might work:

```

sudo update-rc.d disable gdm

```

or try:

```

sudo update-rc.d stop gdm

```

Cipherboy

---

### Post by Krytarik on 2011-05-08
Please see this earlier post:
[http://ubuntuforums.org/showthread.php?p=9644518#post9644518](http://ubuntuforums.org/showthread.php?p=9644518#post9644518)

Greetings.

---

