---
title: "Timezone setting problems"
date: 2009-04-01
forum: General Help
---

### Post by Milambar on 2009-04-01
Having a few problems setting the global timezone on my machine (the timezone for all users). 

dpkg-reconfigure tzdata doesn't work.. Well, it works in that it changes the timezone for the local user, but not the global timezone.

What's happening is:

date returns the correct time.

but a php script that says "<? echo time(); ?>" returns a timestamp thats 5 hours in the past. I'm assuming its because php doesn't run as a real user, and therefore has no local timezone set. 

Could anyone assist?

---

