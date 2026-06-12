---
title: "Logged in or logged out"
date: 2005-11-09
forum: Forum Feedback &amp; Help
---

### Post by Lambert on 2005-11-09
There are times when I click on a link, let's say post a reply to a thread, and the page will come up and say I'm not registered, even though I am logged in. I click and go back a page, click on the same link again and this time it recognizes me.

Ths isn't just with posting a reply, it's other links to. I can't seem to find a pattern. As long as I click back though and try again, the second time it usually recognizes me as being logged in?

Any ideas what might cause this? cookie setting or something else?

---

### Post by ubuntu-geek on 2005-11-09
I'd remove your cookies for the forum and then re-login..

---

### Post by imagine on 2005-11-09
Are you sure that you aren't switching from [http://ubuntuforums.org](http://ubuntuforums.org) to [http://www.ubuntuforums.org](http://www.ubuntuforums.org) or vice versa? Depending on your browser settings cookies set by a certain domain can not be read by another domain.



This leads me yet another suggestion: Would it be possible to redirect [http://www.ubuntuforums.org/*](http://www.ubuntuforums.org/*) to [http://ubuntuforums.org/*](http://ubuntuforums.org/*) (or vice versa)? The same content under two different URLS is confusing for both humans (cookies, visited links, etc) and search engine spiders.
In Apache it's just two lines to set up a "HTTP 301 - Permanently moved" with the RewriteEngine.

---

### Post by Lambert on 2005-11-09
When I say "clikcing on links" I'm not switching sites, just other pages on this site. For example, I was just in the backyard looking at a thread. I clicked to switch to page 2 of the thread and it told me I needed to be a registered user to view this area. I clicked back, clicked on page 2 again and this time could continue reading? 

I'll clean up my cookies.

---

### Post by ubuntu-geek on 2005-11-09
Ok let us know..

---

### Post by Lambert on 2005-11-09
No, after deleting cookies still same problem. This one popped up when I clicked on search and last hour.

A simple back page and click on the link again and no problem???

---

### Post by Lambert on 2005-11-09
It has to be the box I was on or the browser (opera 8.5)

I also noticed my scroll and address bar kept disappearing randomly?

I've switched to another box and no problems here.

---

