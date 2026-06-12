---
title: "mvdial crashes..."
date: 2006-05-26
forum: Desktop Environments
---

### Post by i++ on 2006-05-26
i ran sudo apt-get upgrade and it started to install mvdial... this then hung the laptop, (compaq evo n410c) and then i restarted, ran dpkg --configure -a and it tries again to install it... and it hangs again...

how can i exclude this package for upgrade?

thanks!

i++

---

### Post by i++ on 2006-05-26
is the mvdial a modem app?

---

### Post by wthanna on 2006-05-26
I had the same problem you described.. ran sudo apt-get update, then sudo apt-get dist-upgrade.. system crashed when configuring wvdial.  I think it is crashing trying to detect a winmodem. I have a Dell Inspiron 8100.  I got rid of the message by running Synaptic, then finding wvdial and telling Synaptic to remove it.  It was real late at night, and from what I remember, I had to do this twice..  not absolutely sure about that, but I seem to recall running it twice before it went away.. anyway, I have no need for my modem at the moment (I have DSL) so I can live without the program, untill it is fixed and works with my hardware..  hope this helps.. maybe others will have a fix or better suggestion.  Good Luck!

---

### Post by wilderness wanderer on 2006-05-26
See [this thread]("http://www.ubuntuforums.org/showthread.php?t=182296") for more details.

---

