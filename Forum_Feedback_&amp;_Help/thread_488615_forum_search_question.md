---
title: "forum search question"
date: 2007-06-30
forum: Forum Feedback &amp; Help
---

### Post by wpshooter on 2007-06-30
Our search system has a number of options:

    * All Words - search all words you list in the search box
    * Any Words - search for any of the words in the search box
    * Phrase - search for the complete phrase you type in
    * Boolean - advanced option allows:
    * wordA !wordB (ie word A but NOT Word B in article)
    * wordA (wordB wordC) (ie word A and (Word B and Word C) in article)
    * wordA | (wordB wordC) (ie word A OR (Word B and Word C) in article)
    * Boolean commands supported are:
              | - equivalent to OR
              ! - equivalent to NOT (also - )
              ( ) - subquery allows you to group queries
              & - equivalent to AND - note ANDs are implicit generally not needed

This is fine BUT how do I specify these options ???

Am I supposed to just automatically know this ?

---

### Post by PriceChild on 2007-06-30
> **wpshooter said:**
> * All Words - search all words you list in the search box
    * Any Words - search for any of the words in the search box
    * Phrase - search for the complete phrase you type in
    * Boolean - advanced option allows:Done automatically
> **wpshooter said:**
>      * wordA !wordB (ie word A but NOT Word B in article)
    * wordA (wordB wordC) (ie word A and (Word B and Word C) in article)
    * wordA | (wordB wordC) (ie word A OR (Word B and Word C) in article)
    * Boolean commands supported are:
              | - equivalent to OR
              ! - equivalent to NOT (also - )
              ( ) - subquery allows you to group queries
              & - equivalent to AND - note ANDs are implicit generally not neededThese tell you how to use them?

---

### Post by wpshooter on 2007-06-30
If I want to search for the phrase "out of range", how does this search know to find the occurence of "out of range" and not each and every occurence of out, of and range ?

Do I put, ***Phrase** in front of **out of range** ?

This does not give any explanation of how this works as far as I am concerned or is this one of those things which it is just **assumed** that every computer user knows ?

Thanks.

---

### Post by Mad_Max_1412 on 2007-07-01
Guys,

I search for the word "Zensonic" and it comes back with 3 threads.

One of the threads is about 55 pages long.  How do I get it to go straight to the entry in that thread that contains the word "Zensonic" without going to each page and using the search feature in Firefox to search the page?

Thanks

---

### Post by PriceChild on 2007-07-01
> **wpshooter said:**
> If I want to search for the phrase "out of range", how does this search know to find the occurence of "out of range" and not each and every occurence of out, of and range ?

Do I put, ***Phrase** in front of **out of range** ?

This does not give any explanation of how this works as far as I am concerned or is this one of those things which it is just **assumed** that every computer user knows ?

Thanks.               > ( ) - subquery allows you to group queriesSo.... search for:
```
(out of range)
```It even gave examples of ()'s  and |'s used above it...>      * wordA (wordB wordC) (ie word A and (Word B and Word C) in article)
    * wordA | (wordB wordC) (ie word A OR (Word B and Word C) in article)
> **Mad_Max_1412 said:**
> Guys,

I search for the word "Zensonic" and it comes back with 3 threads.

One of the threads is about 55 pages long. How do I get it to go straight to the entry in that thread that contains the word "Zensonic" without going to each page and using the search feature in Firefox to search the page?

ThanksYou can search an individual thread... go to that thread, then select "Search this thread" at the top right and it will search the individual posts.

---

### Post by ruibernardo on 2007-08-11
> **wpshooter said:**
> Our search system has a number of options:

    * All Words - search all words you list in the search box
    * Any Words - search for any of the words in the search box
    * Phrase - search for the complete phrase you type in
    * Boolean - advanced option allows:
    * wordA !wordB (ie word A but NOT Word B in article)
    * wordA (wordB wordC) (ie word A and (Word B and Word C) in article)
    * wordA | (wordB wordC) (ie word A OR (Word B and Word C) in article)
    * Boolean commands supported are:
              | - equivalent to OR
              ! - equivalent to NOT (also - )
              ( ) - subquery allows you to group queries
              & - equivalent to AND - note ANDs are implicit generally not needed


Gee, I was just looking for that info and didn't find it until now, looking at this thread.

> **wpshooter said:**
> 
Am I supposed to just automatically know this ?

Yes, I agree with wpshooter. 

As a suggestion, at least you could add this info in the "advanced search", so that people that searches for a phrase that have an "and" in it don't get half the forum threads in the response.

---

### Post by PriceChild on 2007-08-11
> **epimeteo said:**
> Gee, I was just looking for that info and didn't find it until now, looking at this thread.That information is for the old search engine, not the one currently being used.

---

### Post by ruibernardo on 2007-08-11
PriceChild, can you tell or point me to where to look to find how the actual search engine works?

---

### Post by ruibernardo on 2007-08-18
Anyone? 

It would be useful to me (and to others, I think) to know how to use the actual search engine more efficiently.

For example, it's a pain to search for "ssh install". 

I know that it's a *bad example*, but try it and you will see what I mean. All posts about installing something (wine/games/upgrading/etc) appear, and there is no (known) way to filter the results...

Thanks in advance.

---

### Post by SpiritIsReality on 2007-08-21
howdy

for what it's worth there's a bit here

vBulletin 3.6.8 mentioned on the bottom of the advanced search page
[http://www.google.ca/search?hl=en&q=vBulletin+3.6.8+search&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=vBulletin+3.6.8+search&btnG=Google+Search&meta=)
a link to the next
[http://www.vbulletin.com/docs/html/](http://www.vbulletin.com/docs/html/)
can check out each page listed at top of this
[http://dev.mysql.com/doc/refman/5.0/en/fulltext-search.html](http://dev.mysql.com/doc/refman/5.0/en/fulltext-search.html)

this works for "..."
[http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+%22free+linux+books+online%22&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+%22free+linux+books+online%22&btnG=Google+Search&meta=)
[http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+%22ssh+install%22&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+%22ssh+install%22&btnG=Google+Search&meta=)
from here
[http://www.googleguide.com/](http://www.googleguide.com/)

trails

---

