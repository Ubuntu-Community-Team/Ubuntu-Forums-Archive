---
title: "anyone else having this problem?"
date: 2006-08-30
forum: Desktop Environments
---

### Post by 1oki on 2006-08-30
I installed gDesklets, and installed the starterbar... All is fine in that field. I added a firefox starter to it and whenever I open firefox, it totaly bypasses the homepage (ubuntu forums) and brings me to the unuversity of Arizona's website. When I click the home button it brings me to ubuntu forums... any suggestions?


l

---

### Post by kaamos on 2006-08-30
You firefox command in the starter is wrong. It sends the command "firefox %u" which normally gets parsed to "firefox" or "firefox http://blaablaa". Firefox uses googles "I'm feeling lucky" for malformed urls and best match for "u" is apparently the University of Arizona. ;)

---

### Post by 1oki on 2006-08-30
Thanks Kaamos! That worked like a charm! :)

---

