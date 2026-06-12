---
title: "Firefox disk access makes it unusable"
date: 2008-05-14
forum: Desktop Environments
---

### Post by khosra on 2008-05-14
Hello.

I am using Hardy with latest updates (hardy-security and hardy-updates) on 64-bit. My firefox 3b5 is almost unusable. Every few seconds, it reads/write to disk on the order of 8mb. I look in .mozilla/firefox under my profile and nothing of that order seems to be getting written. Is there a way I can tell what is going on (what is causing disk access) so I can check the bug reports for solutions?

I have unchecked the safety features in Firefox. I also have checked that urlclassifier3.sqlite is not growing to be very large (a known bug).

I installed firefox-2 but that proved to be difficult so I am using Epiphany for now (which is pretty good).

Thanks.

---

### Post by BlueSkyNIS on 2008-05-14
I have noticed exactly the same behavior while using it under win xp. Don't have a clue what is he doing so hard... :?:

---

### Post by khosra on 2008-05-15
I think the problem was not with Firefox but Google Desktop indexing while I was using the machine. I was downling a PDF using Firefox and Google Desktop seemed to be immediately indexing it. When I turned off indexing in Google Desktop, this problem went away. Anyway, Google Desktop doesn't seem to work with Firefox 3 so I have stopped using it altogether for now.

---

