---
title: "Can't Increase Screen Resolution? (5.04)"
date: 2005-10-19
forum: Desktop Environments
---

### Post by TheSaladCaper on 2005-10-19
EDIT: Ooh, I'm sorry, I didn't see the 5.04 help forum. I'll re-post this there.

I got my free Ubuntu CDs in the mail today (after waiting a good two months :razz:, so far it was completely worth the wait, however) and I eagerly installed them. Everything went smoothly, and so I booted in. However, I was greeted with a lousy 640 x 480 screen resolution, and when I went to increase it, I was not able to.

I know my computer is capable of exceeding this (by far), because I use 1024 x 768   in Windows. Any solution to this problem would be vastly appreciated, and would convert me to a Ubuntu user for life! :)

---

### Post by bored2k on 2005-10-19
From a terminal, type this:
```
sudo dpkg-reconfigure xserver-xorg
``` Then restart. That works sometimes.

---

### Post by aysiu on 2005-10-19
[QUOTE=TheSaladCaper]EDIT: Ooh, I'm sorry, I didn't see the 5.04 help forum. I'll re-post this there.[/quote] Don't bother. I moved it for you.

As for the screen resolution, try this:

[http://ubuntuforums.org/showpost.php?p=129379&postcount=21](http://ubuntuforums.org/showpost.php?p=129379&postcount=21)

---

### Post by racecat on 2005-10-19
[QUOTE=aysiu]Don't bother. I moved it for you.

As for the screen resolution, try this:

[http://ubuntuforums.org/showpost.php?p=129379&postcount=21](http://ubuntuforums.org/showpost.php?p=129379&postcount=21)[/QUOTE]

It probably doesn't apply here, but just a little FYI to tuck away, aysiu: I have a KVM switch and if I switch to the other system while this one boots up, only 640x480 is available. This was kind of an obscure intermittent problem and it took a couple of occurrences to figure it out.

Bill

---

### Post by TheSaladCaper on 2005-10-20
[QUOTE=aysiu]Don't bother. I moved it for you.

As for the screen resolution, try this:

[http://ubuntuforums.org/showpost.php?p=129379&postcount=21](http://ubuntuforums.org/showpost.php?p=129379&postcount=21)[/QUOTE]

Worked like a charm. Thanks a ton!

---

