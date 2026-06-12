---
title: "Procmail and attachment name."
date: 2009-01-06
forum: General Help
---

### Post by shankariyer on 2009-01-06
I'm trying to get the attachment name passed to a perl script, in procmail rc, but
something is screwed up here. Neither does it store the attachment, nor pass
the attachment name to the perl program. What am I doing wrong ?

```

LOGFILE=~proc.log
:0 H c: 
* ^Content-Type: .*;$[ ]*(file)?name=\"?.*\.(xls)\"?$ 
${HOME}/Mail/xls

:0 B
* ^Content-(Disposition|Type):[^;]+;\
(^[     ])?[  ]*(file)?name=\"?.*\/[^"]+
{ ATTACH = $MATCH }
| ~/check.pl

```proc.log keeps saying that "| ~/check.pl" is skipped.

Thanks.

---

