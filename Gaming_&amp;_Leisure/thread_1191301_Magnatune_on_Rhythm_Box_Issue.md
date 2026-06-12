---
title: "Magnatune on Rhythm Box Issue"
date: 2009-06-18
forum: Gaming &amp; Leisure
---

### Post by james.brantley on 2009-06-18
[SIZE=3]I have just recently reinstalled Ubuntu and went to Magnatune in Rhythm Box and where there is usually 3000(I think, some where around there) songs there is now only 70. It is as if I need and update from Magnatune. I have never had this issue before. I can still go to the Magnatune site and listen to/ purchase music but it sure was nice having it all right there in Rhythm Box![/SIZE]

---

### Post by james.brantley on 2009-06-19
[SIZE=3]I woke up this morning and opened up Rhythm Box and Magnatune loaded up 9010 songs compared to 70 songs yesterday! It appears that there might have been an issue with the Magnatune servers. That is my conclusion anyway![/SIZE]

---

### Post by johnbuckman on 2009-06-19
We broke the Magnatune XML export for a few days with some non-english characters in some song names. Those characters needed to get encoded in order to be valid XML.  

With the invalid characters, some XML parsers (including Rhythmbox) were failing to parse it. 

The XML is fixed now, so RB should work fine from now until (until the next bug!)

-john from magnatune.

---

### Post by james.brantley on 2009-06-19
> **johnbuckman said:**
> We broke the Magnatune XML export for a few days with some non-english characters in some song names. Those characters needed to get encoded in order to be valid XML.  

With the invalid characters, some XML parsers (including Rhythmbox) were failing to parse it. 

The XML is fixed now, so RB should work fine from now until (until the next bug!)

-john from magnatune.

[SIZE=3]Thank you very much for the info John. I was really boggled yesterday. I had never experienced that type of problem before. Thanks for the "official" report![/SIZE]

---

