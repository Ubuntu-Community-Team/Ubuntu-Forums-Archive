---
title: "Forum Search"
date: 2010-07-08
forum: Forum Feedback &amp; Help
---

### Post by cj.surrusco on 2010-07-08
I don't know about everybody else, but I've never been able to use the forum search effectively. When I search, it sorts the threads by last post time. It doesn't give you an option to sort by relevancy or anything like that. 

So whenever I search, it often comes up with irrelevant threads. What are some easy ways to find the most useful and relevant threads?

---

### Post by lisati on 2010-07-08
Both Google and Yahoo allow you to add "site:ubuntuforums.org" to your list of search keywords. These can result in more useful results being displayed.

---

### Post by cj.surrusco on 2010-07-08
That works pretty well. Thanks.

---

### Post by SoFl W on 2010-07-11
Or you could just add ubuntu forms to firefox's search bar...

as root goto 
/usr/lib/firefox-addons/searchplugins
Create a file called "ubuntu_search.src" and enter this:

> 
<search 
 name="Ubuntu-Forums"
 method="GET"
 action="http://www.google.com/search"
 queryCharset="utf-8"
> 
  <input name="q" user>
  <input name="sitesearch" value="ubuntuforums.org">
</search>Save the file, restart Firefox.

---

