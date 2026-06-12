---
title: "Adding startup items manually?"
date: 2009-03-20
forum: General Help
---

### Post by tacomodo on 2009-03-20
Hi

Was reading this post, but it wouldn't let me reply to it, so making a new one
[http://ubuntuforums.org/showthread.php?t=602810](http://ubuntuforums.org/showthread.php?t=602810)

How do I add startup items manually, like for instance pidgin?

Would it work to make a symlink to pidgin in rc4.d (rc5.d?)?

Where exactly is it added if I use System -> Preferences -> Session?

---

### Post by kanikilu on 2009-03-20
If you use System > Preferences > Session, I believe it gets added to ~/.config/autostart/

---

### Post by tacomodo on 2009-03-21
Thanks, found it.

It seems ~/.config/autostart/ is only the ones you specify yourself, though. Any idea where the rest are?

---

### Post by sekinto on 2009-03-21
Globally added ones might be in /usr/share/autostart and /usr/share/gnome/autostart.

Note:
You will need to be root to modify files in these folders and these changes will affect all users.

---

