---
title: "New tab with Unanswered Posts"
date: 2018-05-09
forum: Forum Feedback &amp; Help
---

### Post by ank2 on 2018-05-09
Only when I click *Quick Links* and then *Unanswered Post* only this opens in a new tab in the browser which I find quite annoying because I use this a lot, piling up new tabs. Something wrong with my setting I cannot find or does it "work as designed"?

---

### Post by thenailedone on 2018-05-09
Google Chrome up-to-date and I have the same happen. I don't believe this is a bug but a feature ;)

---

### Post by &amp;KyT$0P# on 2018-05-09
It's by design -
```
<li id="link_mje2_914"><a [COLOR="#FF0000"]**target="_blank"**[/COLOR] href="search.php?do=process&amp;type[]=1&amp;replyless=1&amp;replylimit=0">Unanswered Posts</a></li>
```

You could try a user script -
```
document.getElementById('link_mje2_914').firstChild.removeAttribute('target');
```

---

### Post by coffeecat on 2018-05-09
Neither a bug nor a feature, but simply the way that was configured. It's been like that for years.

Since all the other selections under quick links open in the same tab I've reconfigured it so that unanswered posts does too, if only for consistency. 

I notice that some of the choices under the Forum Community tab open in new tabs and some don't, so there's inconsistency there too. I'll take this up with the other admins so that we can get a consensus on tidying this up. The truth is that the Navigation Tabs were set up when the forum was upgraded from vbulletin 3 to vbulletin 4 quite a few years ago, and they've been tinkered with on an as needed basis since then, and I think personal preferences have crept in depending on which admin did the tinkering.

@ank2, thanks for noticing this and bringing it up.

---

### Post by ank2 on 2018-05-09
Okay, I looked into the HTML source and saw the "target=_blank" bought thought I might have this set up in my settings here. Apparently not as others also have this. The question is still **why** did the forum maintainers choose to have only this link in a new tab?

---

### Post by coffeecat on 2018-05-09
> **ank2 said:**
> Apparently not as others also have this. The question is still **why** did the forum maintainers choose to have only this link in a new tab?

Did you read my post, the one before this one?

---

### Post by ank2 on 2018-05-10
> **coffeecat said:**
> Did you read my post, the one before this one?

No. Your post didn't show up before I wrote mine. After that I logged out only to see it now.

Thanks for the "fix". :p

Is it okay to mark this "Solved" then?

---

### Post by deadflowr on 2018-05-10
> Is it okay to mark this "Solved" then?

your thread
your choice.
if it's solved for you then yes.

---

