---
title: "Games asking for a CD..."
date: 2006-08-19
forum: Gaming &amp; Leisure
---

### Post by SZF2001 on 2006-08-19
So some games don't come with the option of a full install.

They keep asking for a CD, when, in fact, there is a CD in the disk drive.

Is there something I missed? What needs tweaking here?

---

### Post by Sandlst on 2006-08-19
I belive you have to do this to get it to see the cd as a cd instead of a mounted harddrive: open winecfg```
winecfg
``` Go to the 'Drives' tab, click autodetect, highlight whichever drive is mapped at /dev/cdrom0, click 'Show Advanced' and change the 'Type' to CD-ROM, then click Apply and OK.  Post back if you still have problems.

---

