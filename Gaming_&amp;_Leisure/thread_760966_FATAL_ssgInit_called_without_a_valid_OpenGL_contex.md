---
title: "FATAL: ssgInit called without a valid OpenGL context."
date: 2008-04-20
forum: Gaming &amp; Leisure
---

### Post by ekravche on 2008-04-20
I'm getting this error when trying to run supertuxkart.

FATAL: ssgInit called without a valid OpenGL context.

Any ideas how I can fix this problem?

Thank you in advance.

---

### Post by ekravche on 2008-04-20
Solved just changed xorg.conf and set 
> 
DefaultDepth    24

Mine was set to 16 before.

---

### Post by randomlogic on 2008-08-16
I've got an unusual variation of this problem.  My own account on my laptop has no trouble starting supertuxkart.  But if my son logs in with his account, he gets the ssgInit error.

I checked xorg.conf as mentioned in the previous post and that wasn't it.  And since this problem seems to be account-specific, I'm not surprised.

The only real difference between the accounts is that his does not have administrator privileges.  Oddly, supertuxkart used to work from his account.

Does anyone else have any ideas?

---

### Post by randomlogic on 2008-08-18
I have further information on this problem.  I have a second machine on which Ubuntu was loaded, but on which supertuxkart had not yet been run.

There are 4 user accounts on the machine.  The first account to try was able to start the program.  But then ALL of the other accounts got the OpenGL error.

In this case, an account without admin privileges was the one that worked.  So now we have more to go on.  I have to wonder if supertuxkart is creating a file somewhere that is tied to the first user and then trying to use it for other users.

Hmmmmm.

---

