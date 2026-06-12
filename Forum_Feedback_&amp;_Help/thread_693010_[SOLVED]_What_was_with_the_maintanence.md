---
title: "[SOLVED] What was with the maintanence?"
date: 2008-02-10
forum: Forum Feedback &amp; Help
---

### Post by -grubby on 2008-02-10
What was the UF maintenance going on? oh and, in the future, would you be ever so kind to PM us or something before it goes down. I was going crazy for 3 hours not having my forums :cry:

---

### Post by Danni on 2008-02-10
Also, next time can you try to open on time? :D

---

### Post by fedex1993 on 2008-02-10
okay nahtan isnt that a lie more like 2 hours lol but if yall where inside #ubuntuforums everyone went crazy

---

### Post by ser_enity on 2008-02-10
lol, I'm glad I wasn't the only one franticly clicking refresh and going through withdrawls...

---

### Post by amingv on 2008-02-10
Every so often servers/databases need maintenance. No biggie. And I see no point in PMing if you might not read it until the server is back online.

---

### Post by amingv on 2008-02-10
> **ser_enity said:**
> lol, I'm glad I wasn't the only one franticly clicking refresh and going through withdrawls...

I was into this:

[ATTACH]59304[/ATTACH]

Sad, really...

---

### Post by ser_enity on 2008-02-10
What's sad is that I really was on that page #-o

---

### Post by ubuntu-geek on 2008-02-10
We needed to do some cleanup on the database as well as take a snapshot and import into a test database for our migration to vb 3.7. When its ready people will be able to help us beta test. I apologize for the downtime but it takes awhile when working with a 10gb+ database :)

---

### Post by -grubby on 2008-02-10
> **ubuntu-geek said:**
> We needed to do some cleanup on the database as well as take a snapshot and import into a test database for our migration to vb 3.7. When its ready people will be able to help us beta test. I apologize for the downtime but it takes awhile when working with a 10gb+ database :)

ah it's ok. I understand. I'm off to mark this as solved...

---

### Post by kevdog on 2008-02-10
Never take down the forums again...It was maddening I tell you!

---

### Post by FuturePilot on 2008-02-10
At least there was #ubuntuforums to help fill the void. If it wasn't for #ubuntuforums I don't know what I would have done. :lolflag:
It was a blast in there :guitar:

---

### Post by hyper_ch on 2008-02-11
10+ GB db? That's insane...

---

### Post by popch on 2008-02-11
> **hyper_ch said:**
> 10+ GB db? That's insane...

A very rough guesstimate (or - as the Swiss call it - a milk booklet reckoning):

Threads:          675231
Posts:            4296855
Members:        500343

total entities: 5472429

A record size of about 2kB per entity lands you very near to 10+GB, and that's not even counting the complex associations between entities such as subscribed threads.

---

### Post by misfitpierce on 2008-02-11
> **kevdog said:**
> Never take down the forums again...It was maddening I tell you!

lol

---

### Post by hyper_ch on 2008-02-11
> **popch said:**
>  a milk booklet reckoning):
I didn't know there was an english equivalent of our "Milchbüechlirechnig" ^^

> **popch said:**
> 
Threads:          675231
Posts:            4296855
Members:        500343

total entities: 5472429

A record size of about 2kB per entity lands you very near to 10+GB, and that's not even counting the complex associations between entities such as subscribed threads.
But still, a 10 GB db is still huge ;)

---

