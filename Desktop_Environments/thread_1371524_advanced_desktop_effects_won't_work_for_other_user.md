---
title: "advanced desktop effects won't work for other users"
date: 2010-01-03
forum: Desktop Environments
---

### Post by onenall on 2010-01-03
for the primary user, me, installer of system, all effects work great.

however when i try to enable them for the rest of the users it does not work. they only get basic. normal or advanced cannot be enable. ( I think it worked once but only for a very short period of time for one of the users.) what seems to be the problem?


i want everybpdy to have nice effects.



thanks for the help and i am sure this problem has been tackled before. im just lookiing for a quick answer,.

thanks

---

### Post by mcduck on 2010-01-04
The reason is actually quite simple. The desktop effects require direct access to your graphics card, and only one application can have that at a time. So once one user takes the direct rendering access, the rest can't do the same.

If you log out and then log in as another user the new user should be able to use desktop effects. It's just that you can't have two users logged in at the same time and using the effects.

(Windows doesn't have such problem because it doesn't actually keep all user's desktops fully running in the background. Linux does, since the other user's could just as well be using a remote session or another graphics card+keyboard+mouse or something, so stopping one user's session when another one logs in wouldn't make any sense)

---

