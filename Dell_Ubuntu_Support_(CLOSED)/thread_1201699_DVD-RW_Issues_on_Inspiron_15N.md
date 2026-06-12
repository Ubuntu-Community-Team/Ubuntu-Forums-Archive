---
title: "DVD-RW Issues on Inspiron 15N"
date: 2009-07-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tmountain on 2009-07-01
Hi all, just got a new Inspiron 15N laptop yesterday. The first thing I tried to do after taking it out of the box was to burn a recovery DVD in case I ever wanted to roll back to factory settings. I initially tried to use Brasero, and it crashed on me. My dmesg output shows a lot of these type messages:

```
Buffer I/O error on device sr0
```

There's nothing in the BIOS config to change the DVD drive from auto to UDMA or anything along those lines. I've upgraded to 9.04, and the messages are still sporadically appearing in the logs. Do you guys think I should RMA the unit? It can read DVD and CD media fine, but I'm afraid there's a defect in the burning.

---

### Post by tmountain on 2009-07-01
I did a clean install of 9.04, and the problem seems to be resolved.

---

