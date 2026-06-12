---
title: "Need to Trick Ubuntu"
date: 2009-02-15
forum: General Help
---

### Post by billybob9187 on 2009-02-15
is there a way to trick ubuntu to think that the 3d acceleration drivers are installed?

Reason being is that i have dont this [http://ubuntuforums.org/showthread.php?t=884161](http://ubuntuforums.org/showthread.php?t=884161) across 4 screens and the xgl server has disabled the driver that ubuntu requests. I need to get this working so i can play games. Both linux games and Wine games complain of errors in 3d rendering. 

Thx in advance

---

### Post by Twilight in Zero on 2009-02-15
You're not going to be able to play games on xgl. You usually can't play games on compiz with the standard x server, either; the compositing creates glitches in some games.

You could try starting a standard xserver alongside xgl for your games. Try searching for "xgl games" on the ubuntu forums (without the quotes).

---

