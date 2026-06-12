---
title: "Regular Expression Problem (challenge?)"
date: 2009-03-10
forum: General Help
---

### Post by gvanto on 2009-03-10
I am having some trouble wiht the following, I'm trying to create a regular expression whichi will match
"November 07" or "November '07" but NOT "November 07th 2004"

This is in php and I have so far:

[PHP]

"/((Jan|Feb|Mar|Apr|May|Jun|Jul|Aug|Sep|Sept|Oct|Nov|Dec|January|February|March|April|May|June|July|August|September|October|November|December)([^\w])*(\d)+(\b) )/i"

[/PHP]

which works for November '07 but unfortunately also picks up "November 07 2007"

Help would be greatly appreciated,
gvanto

---

