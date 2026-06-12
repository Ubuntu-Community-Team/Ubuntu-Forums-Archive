---
title: "[SOLVED] adding commands to shutdown?"
date: 2008-12-07
forum: General Help
---

### Post by Arenlor on 2008-12-07
I have a couple of commands I wish to add to my shutdown routine and was wondering how I add them.

---

### Post by Arenlor on 2008-12-21
Is there a way to add a command to the shutdown sequence?

---

### Post by gTinker on 2008-12-21
[QUOTE=Arenlor]Is there a way to add a command to the shutdown sequence?[/QUOTE]

I remembered seeing something about this recently so I did a forum search with the keywords, script and shutdown. The following thread has the information you are asking for.
 [http://ubuntuforums.org/showthread.p...cript+shutdown](http://ubuntuforums.org/showthread.p...cript+shutdown)

---

### Post by dcstar on 2008-12-22
> **Arenlor said:**
> I have a couple of commands I wish to add to my shutdown routine and was wondering how I add them.

Shutdown runs all things in the /etc/rc0.d directory (reboot rc6.d), you can look as what is already in those locations and use them as an indication of what you need to do for your own purposes.

---

