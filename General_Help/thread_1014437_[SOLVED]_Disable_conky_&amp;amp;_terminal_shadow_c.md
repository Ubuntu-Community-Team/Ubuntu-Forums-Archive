---
title: "[SOLVED] Disable conky &amp;amp; terminal shadow code not working?"
date: 2008-12-17
forum: General Help
---

### Post by xHero on 2008-12-17
I have this:

```
(any) & !(Title=conky) & !(Title=Terminal)
``` in the Shadow Windows field of "Window Decoration".  However, after restart these windows still have shadows.

What is wrong with my code?

Thanks,
Hero

---

### Post by Wartender on 2008-12-17
that's cause they're not the names of the applications, but i think the terminal is <username>@<username>-desktop: ~
although i'm pretty sure this changes when you cd somewhere so it's pretty useless.
(you can make a new profile for the terminal (make it a relly weird name, or it'll take shadows out of other windows with that name as part of their name) and set it as your default, and then it'll work (if you set the profile name)

---

### Post by xHero on 2008-12-17
Ah yes, I found it.  Correct code is:
```
(any) & !(name=Terminal) & !(name=Conky)
```

Thank You.

---

