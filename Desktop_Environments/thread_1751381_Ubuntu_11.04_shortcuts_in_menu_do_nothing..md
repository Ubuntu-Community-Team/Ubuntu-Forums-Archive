---
title: "Ubuntu 11.04 shortcuts in menu do nothing."
date: 2011-05-06
forum: Desktop Environments
---

### Post by zaeb on 2011-05-06
Not sure if it's something I did/didn't do but when I click in the upper left corner to bring up the menu (with Media Apps, Internet Apps, More Apps & Find Files) clicking on any of those doesn't prompt a response, no error is given either. When I type in the top bar something such as Terminal it doesn't do anything (although I can still get to Terminal with ctrl+alt+t). 

Any ideas?

---

### Post by zaeb on 2011-05-07
Bump.

---

### Post by kerry_s on 2011-05-07
clean install or upgrade ?
10.10 upgrades have not been going well.

---

### Post by zaeb on 2011-05-07
It was a clean install. It was working fine for awhile but I'm not sure why they stopped working, or how to get the functions back.

---

### Post by mc4man on 2011-05-07
You may want to ck. that you have the unity-place-applications and unity-place-files packages installed

---

### Post by zaeb on 2011-05-07
That was it! Thanks.

---

### Post by mc4man on 2011-05-07
> **zaeb said:**
> That was it! Thanks.

Now that you've got them back a small warning
11.04 (unity login in particular) has a number of current memory leaks
One on them involves compiz and the use of the dash and places - the initial use of any of the various functions  will cause a bit of a memory bump.

After that there'll be a per use increase, while fairly small, (1-2 MB per use), can add up after a while depending on usage and time online. Worth checking every once and a while
(there are other leaks that also can come into play

---

### Post by zaeb on 2011-05-08
> **mc4man said:**
> Now that you've got them back a small warning
11.04 (unity login in particular) has a number of current memory leaks
One on them involves compiz and the use of the dash and places - the initial use of any of the various functions  will cause a bit of a memory bump.

After that there'll be a per use increase, while fairly small, (1-2 MB per use), can add up after a while depending on usage and time online. Worth checking every once and a while
(there are other leaks that also can come into play

Thanks for the heads up!

---

