---
title: "Search ID's expire too quickly"
date: 2006-08-19
forum: Forum Feedback &amp; Help
---

### Post by hopstah on 2006-08-19
I don't know if this is anything that can be changed, but it seems that the search id's on the site expire too quickly.  Maybe this is just something within vbulletin and can't be changed, but it's annoying.

for example, i often use the 'get unanswered posts' search function to see how i can help out on the forums.  i might open a thread or three on the first page to see if i know how to fix the person's problem, and then proceed on to page 2 of the search results only to find that my search has already been flushed out of the database.  i have to then re-search, which pulls up the first page again, and then i can click through to the second page.  this wastes more bandwidth than had my search id just stayed active a while longer.  it's just an annoyance and maybe something that can be tweaked.

---

### Post by hopstah on 2006-08-30
this is really an obnoxious problem.  from my experimentation, i have discovered that the servers keep less than 19 search queries in memory before they get flushed and invalidated.  for a forums that gets as much traffic as this one does, i think that is way too few.

---

