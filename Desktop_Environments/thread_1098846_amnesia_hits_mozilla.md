---
title: "amnesia hits mozilla"
date: 2009-03-17
forum: Desktop Environments
---

### Post by engine on 2009-03-17
Heron, Mozilla 3.0.7, two users ...

for user A (me!), Mozilla has suddenly decided not to store any history; no bookmarks, not even Back links

for user B, no problem: Mozilla functions perfectly

Hints and tips on how to resolve this will be welcome. The "delete this file" suggestion on the Mozilla helps didn't get me anywhere.

---

### Post by Zorael on 2009-03-17
What file did the Mozilla help suggest you delete?

I'd try the following.
```
$ mv ~/.mozilla/firefox ~/firefoxbackup
```
That should make it recreate your Firefox profile and all its settings, including wiping extensions and bookmarks. If it works, just delete the **firefoxbackup** directory now in your home.

---

### Post by engine on 2009-03-20
<sigh> Trying to find the Mozilla helps that said "delete [fname]", I came across the tip that it could have been permissions; and sure enough, starting Mozilla as su just once had reset the permissions on the bookmarks file.

Put the permissions back as they should be, and no more problem with bookmarks - but I never did find that Mozilaa help page again ...

---

