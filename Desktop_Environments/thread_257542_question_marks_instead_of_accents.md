---
title: "question marks instead of accents"
date: 2006-09-14
forum: Desktop Environments
---

### Post by codas on 2006-09-14
Dear All!

When I open pine (to read emails) instead of accents I get question marks in the screen (white question marks inside a black circle).  Do you know how may I fix this problem?

Thanks a lot.

Best regards,
Daniel

---

### Post by Ramses de Norre on 2006-09-14
I think this is a character encoding or font issue. Have you checked the properties for these?

---

### Post by codas on 2006-09-14
Thanks for the reply... but the problem is more general... the problem does not happen only with pine.  For instance, if I do a "cat" of a file when logged in a remote machine, the accents usually also appear as question marks... is there a way to avoid this problem?

More precisely:

Machine ilha: 

[user@ilha ~]$ locale
LANG=en_US
LC_CTYPE="en_US"
LC_NUMERIC="en_US"
LC_TIME="en_US"
LC_COLLATE="en_US"
LC_MONETARY="en_US"
LC_MESSAGES="en_US"
LC_PAPER="en_US"
LC_NAME="en_US"
LC_ADDRESS="en_US"
LC_TELEPHONE="en_US"
LC_MEASUREMENT="en_US"
LC_IDENTIFICATION="en_US"
LC_ALL=

Machine copa:

user@copa:~$ locale
LANG=pt_BR.UTF-8
LANGUAGE=en_US:en_GB:en
LC_CTYPE="pt_BR.UTF-8"
LC_NUMERIC="pt_BR.UTF-8"
LC_TIME="pt_BR.UTF-8"
LC_COLLATE="pt_BR.UTF-8"
LC_MONETARY="pt_BR.UTF-8"
LC_MESSAGES="pt_BR.UTF-8"
LC_PAPER="pt_BR.UTF-8"
LC_NAME="pt_BR.UTF-8"
LC_ADDRESS="pt_BR.UTF-8"
LC_TELEPHONE="pt_BR.UTF-8"
LC_MEASUREMENT="pt_BR.UTF-8"
LC_IDENTIFICATION="pt_BR.UTF-8"
LC_ALL=


When I do an ssh from copa to ilha, and "cat" a file with accents, the accents do not appear properly... is it possible to avoid this?

Thanks in advance!


Best regards,

Daniel

---

### Post by kafkaian on 2006-10-23
These are issues that people are just not responding to and I've seen many unresolved threads regarding fonts and accents.

As former Windows users many people, it seems, turn to Ubuntu. However, coming from an environment where character sets, fonts and alternative accents are not a problem I really think the developers need to address these issues more formally ](*,)

---

