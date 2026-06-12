---
title: "Magnatune Issue Solved"
date: 2009-06-19
forum: General Help
---

### Post by james.brantley on 2009-06-19
[SIZE=3]For anyone who experienced any problem with Magnatune yesterday here is the official word[/SIZE].

> **johnbuckman said:**
> We broke the Magnatune XML export for a few days with some non-english characters in some song names. Those characters needed to get encoded in order to be valid XML. 

With the invalid characters, some XML parsers (including Rhythmbox) were failing to parse it. 

The XML is fixed now, so RB should work fine from now until (until the next bug!)

-john from magnatune.

---

