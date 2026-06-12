---
title: "Problem - Changed my user's group?"
date: 2006-07-21
forum: Desktop Environments
---

### Post by Kaiousama on 2006-07-21
I was adding my user account to the www-data group so certain default permissions wouldn't force me to keep using sudo to move some files around that weren't critical.

However, I ended up making my user ONLY a part of www-data group I believe, because right now I can't seem to execute sudo correctly.  If I use it, nothing happens!  It's as if the command was ignored (no error).

Is there any way to restore my user to it's defaults, because right now I'm locked out of being able to do anything as root!

---

### Post by hw-tph on 2006-07-21
Boot into rescue mode. You will find yourself at the console as root. Add yourself to the proper groups (admin group gives sudo access in the default Ubuntu setup). In cases such as this I prefer simply editing /etc/group (back it up first...!).


Håkan

---

### Post by Kaiousama on 2006-07-21
Thanks, I got it all fixed once I looked up how to get into the rescue mode.

---

