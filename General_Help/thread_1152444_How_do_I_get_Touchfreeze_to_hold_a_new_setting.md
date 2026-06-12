---
title: "How do I get Touchfreeze to hold a new setting?"
date: 2009-05-07
forum: General Help
---

### Post by Shawn K on 2009-05-07
I'm using Touchfreeze on 8.10 to help me with the cursor jumping problem.  For the most part, it works as advertised.  

I've noticed one recurring problem.  I like to run Touchfreeze with the delay turned all the way down as low as it will go.  I'll click "Apply", and everything works fine until the next time I power up the computer.  When I do, Touchfreeze goes back to the default setting of .50 seconds of delay.  Re-adjust, works fine until next power-on.  Lather, rinse, repeat.

How do I get Touchfreeze to apply my settings permanently?

---

### Post by 123456789123456789123456 on 2009-05-07
It should automatically keep the settings permintly after you set them, The only reason it would not, is if for some strange reason, it thinks you don't have permission to make the changes.

Could also result in a permission problem with the files it writes this new settings to.  If they have incorrect permissions, that could cause problems.

Check the file system, and attempt to check if all permissions on machine are correct.

If that comes up that everything is fine, the only other thing I can think of is that the program is malfunctioning, attempt to completely remove the program, and reinstall.

---

### Post by Shawn K on 2009-05-08
It would appear that it's a permissions issue.  I checked usr/bin/synclient, and all of the permissions were listed under root.

This may be the dumbest question ever (and please excuse my ignorance... learning here), but how do I log in as root so that I can change those permissions?

---

