---
title: "gnome desktop fails at logon attempts  (kde is fine)"
date: 2006-06-13
forum: Desktop Environments
---

### Post by Shonkin57 on 2006-06-13
**Hardware:** Compaq Presario laptop 2545US w/ pcmcia hawking card (using rt2500 chip set; Ubuntu runs this best of any linux flavor I've seen).

**Software installed:** Ubuntu (gnome); Kubuntu (kde). 

**Software uninstalled:** Enlightenment, which once I installed it, started coming up on kde's desktop! So I removed it. And (I think) this is where the problem came in.

**Problem:** though kde is running great, gnome now refuses to log me in at all. When I try to log in, I am confronted with a default color background and the taskbars flashing (in about 1 to 3 second pulses) on and off. The situation remains until I hit ctrl-alt-backspace to kick myself out of the session. 

**Solutions attempted: **Reinstalled ubuntu desktop. No change. Reinstalled large parts of the gnome system, incl. libraries. No change. I installed another user name and logged into gnome. Huh? It came up fine. Okay, so I know gnome probably isn't broken itself. Likely human error contributed to this mess. I tried renaming .gnome2, .gnome and a few other directories, then copying the directories of the other user I'd created into my own home directory. Hmm. How DO you change the user permissions, though.... I oughta have that down after all this time, but do not. And would that work anyway? And would I bust links that kde needs by messing that much with gnome?

**Help?** Any solutions / comments would be greatly appreciated. I really like Ubuntu, and merely want both kde and gnome fully functional. I sometimes get the feeling that they really aren't all that good of neighbors.

Thank you in advance.

---

### Post by rbalfour on 2006-06-13
[QUOTE=Shonkin57]**Hardware:** Compaq Presario laptop 2545US w/ pcmcia hawking card (using rt2500 chip set; Ubuntu runs this best of any linux flavor I've seen).

**Software installed:** Ubuntu (gnome); Kubuntu (kde). 

**Software uninstalled:** Enlightenment, which once I installed it, started coming up on kde's desktop! So I removed it. And (I think) this is where the problem came in.

**Problem:** though kde is running great, gnome now refuses to log me in at all. When I try to log in, I am confronted with a default color background and the taskbars flashing (in about 1 to 3 second pulses) on and off. The situation remains until I hit ctrl-alt-backspace to kick myself out of the session. 

**Solutions attempted: **Reinstalled ubuntu desktop. No change. Reinstalled large parts of the gnome system, incl. libraries. No change. I installed another user name and logged into gnome. Huh? It came up fine. Okay, so I know gnome probably isn't broken itself. Likely human error contributed to this mess. I tried renaming .gnome2, .gnome and a few other directories, then copying the directories of the other user I'd created into my own home directory. Hmm. How DO you change the user permissions, though.... I oughta have that down after all this time, but do not. And would that work anyway? And would I bust links that kde needs by messing that much with gnome?

**Help?** Any solutions / comments would be greatly appreciated. I really like Ubuntu, and merely want both kde and gnome fully functional. I sometimes get the feeling that they really aren't all that good of neighbors.

Thank you in advance.[/QUOTE]


rm .gnome2 and .gnome then re-login, this will re-create a FRESH setting file for your account.

REF. chmod to change RWX permission, chgrp to change group permissions, chown to change user permission.

$ man chmod
$ man chgrp
$ man chown
for more info.

---

### Post by ayoli on 2006-06-13
chown can also set group ie:

chown username.groupname /path/to/file

---

### Post by Shonkin57 on 2006-06-13
rbalfour,

Wouldn't renaming the .gnome2 and .gnome directories, as I did, do the same thing (and more safely) than rm-ing them out of existence? I mean, that was my hope originally, that gnome would re-start itself with a virgin setup when those files weren't found. But it didn't work, which led me to think there's other files it must read as well. ???

---

### Post by ayoli on 2006-06-13
i think you should move or remove .gconf* dirs also

---

### Post by Shonkin57 on 2006-06-13
ayoli, **THAT WORKED! **Thanks so much!

I didn't even bother moving .gnome2 and .gnome this time -- since moving them did nothing the last time out. I merely did as you suggested, moved .gconf, and BAM! got the virgin gnome desktop. I really need to remember that trick!

Again, thanks. And I read your long post on trolls with amazement and appreciation. For my 2 cents, Ubuntu (and any linux / GNU distro and/or program) is only there to be appreciated and (if I can help, which is doubtful) improved. Constructively. Rants once in a while are fine, but overall are merely wastes of time and oxygen.

---

