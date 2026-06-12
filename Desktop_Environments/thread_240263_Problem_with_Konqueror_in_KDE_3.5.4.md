---
title: "Problem with Konqueror in KDE 3.5.4"
date: 2006-08-20
forum: Desktop Environments
---

### Post by Kimm on 2006-08-20
Since upgrading to KDE 3.5.4 Konqueror has been acting strangely.

There is no better way to describe the error than by posting a screenshot...

[[IMG]http://img237.imageshack.us/img237/5972/spkim1lw1.th.png[/IMG]](http://img237.imageshack.us/my.php?image=spkim1lw1.png)

---

### Post by Kimm on 2006-08-20
//bump\\

---

### Post by lupine_nickt on 2006-08-20
I interpret that as foobar'd MIME types. Basically, konq. doesn't realise that it should be opening the page, so it's asking you what to do. Something similar happened to me while making firefox my default browser, once.

In konq., check Settings->Configure Konq.->File Associations, and make sure that konq. is listed as being able to open .php, .html, etc...

xF,

...Nick

---

### Post by Kimm on 2006-08-20
I fixed it.

Settings -> Configure Konqueror -> File Associations

search for html

text -> html -> Embedding

select "Show file in embedded viewer" and make sure that KHTML is at the top of the "Services Preference Order" list, then click Apply.

:-D

---

