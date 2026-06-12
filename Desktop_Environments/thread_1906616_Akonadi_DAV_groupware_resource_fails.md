---
title: "Akonadi DAV groupware resource fails"
date: 2012-01-09
forum: Desktop Environments
---

### Post by zynex on 2012-01-09
Hi.

I have tried to get Akonadi DAV groupware resource to work for a while not, without any luck. Tryed to add support for both Google and Memotoo (CardDAV and CalDAV), but nothing works. It always report error 401.

I use kdepim 4.7.4 (from Kubuntu Updates PPA).

Anyone else have problem with this, and maybe a solution for it :)

---

### Post by zynex on 2012-01-09
Found the problem why this didn't work, language! When adding a DAV resource when having Swedish system language, it will fail. When changing to English system language, it worked. This is a very confusing and annoying bug I must say :P

Wonder how to fix this tho...?

---

