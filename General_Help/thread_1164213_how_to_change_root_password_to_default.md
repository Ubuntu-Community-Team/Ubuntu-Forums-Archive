---
title: "how to change root password to default ??"
date: 2009-05-19
forum: General Help
---

### Post by chinmaya_n on 2009-05-19
I recently changed my root password.... I would like to keep it as none.... I mean with out any password for root.... i.e like it is freshly installed one (with out any root password)....

can any one help me...!!):popcorn:

---

### Post by Soul-Sing on 2009-05-19
$sudo passwd -l root

If you want to work on a root console you'd better use the following command

$sudo -i

---

