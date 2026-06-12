---
title: "How to clear sessions?"
date: 2008-08-26
forum: Desktop Environments
---

### Post by JayUK20 on 2008-08-26
I've got windows opening up everytime I reboot and I want them to stop popping up, how do I clear things up?

---

### Post by akudewan on 2008-08-26
Look under System > Preferences > Sessions > Session Options. Uncheck the 'Automatically remember..' box if it is checked.

---

### Post by JayUK20 on 2008-08-26
I have unticked that option but I am still getting the same issues, I was thinking maybe clearing some sort of cache?

---

### Post by kellemes on 2008-08-26
> **JayUK20 said:**
> I have unticked that option but I am still getting the same issues, I was thinking maybe clearing some sort of cache?

As far as I know *akudewan* is correct.
Have you rebooted since?

Edit:
I'm on Debian but surely it's the same with Ubuntu..
The sessionfile used by Gnome is ~/.gnome2/session
You can rename it and see if it clears the "cache", if you get trouble, simply rename it back.

---

### Post by lswest on 2008-08-26
also, make sure the list of stuff in the sessions box doesn't have any of those windows listed to start on boot.  Otherwise I don't see what the problem would be.

---

### Post by JayUK20 on 2008-08-26
I've cleared the start up stuff but they just reappear, I will try the session file and see if that clears things up, I will post back.

---

### Post by JayUK20 on 2008-08-26
Ok, the renaming of session file seemed to do the trick, though another problem has come about. When I edit my timezone to get the weather to display in the bottom right hand corner, the weather display disappears on reboot.

---

