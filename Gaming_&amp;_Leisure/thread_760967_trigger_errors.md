---
title: "trigger errors"
date: 2008-04-20
forum: Gaming &amp; Leisure
---

### Post by ekravche on 2008-04-20
When trying to run trigger I get the following error.

> Failed to create window or set video mode
SDL error: Couldn't find matching GLX visual


I was able to run this game in ubuntu 7.10, but now that I have upgraded to 8.04, the above error persists.

Any help would be appreciated.

---

### Post by ekravche on 2008-04-20
Solved just changed xorg.conf and set 
> 
DefaultDepth    24

Mine was set to 16 before.

---

