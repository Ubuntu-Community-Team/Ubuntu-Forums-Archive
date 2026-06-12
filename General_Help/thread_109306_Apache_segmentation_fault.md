---
title: "Apache: segmentation fault?"
date: 2005-12-28
forum: General Help
---

### Post by Hirs on 2005-12-28
Hi!

I'm doing some developments with apache+php+mysql and eGroupware, a php CRM, but I'm unable to use some modules like calendar or infolog, that are big ones, smaller modules like addressbook works fine.

Whenever I access to those modules I get this error in the apacher error log:

[notice] child pid 24681 exit signal Segmentation fault (11)

It's fustrating because I have tried apache+php4/php5, apache2+php4/php5 and the latest stable versions of apache and php compiled by own.

I think it could be something external to apache or php, but other apps like mambo just works... the only difference may be in php's mysqli extension that is used by eGroupWare

By the way, it's very extrange see apache segfaulting..

I'm using kubuntu breezy with KDE 3.5

Any hint?

---

