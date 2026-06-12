---
title: "Quick Links-&gt;Find All My Threads is broken (search results page)"
date: 2014-12-11
forum: Forum Feedback &amp; Help
---

### Post by kpatz on 2014-12-11
When I select "Find All My Threads" from the Quick Links menu on the Search Results page, I get the message: "Please add more constraints to your search. Searches that return all or most of the database are a bad idea.".

"Find All My Posts" works fine.  When I compared the URLs generated, it appears that the "Find All My Threads" omits the userid value.  If I manually insert my userid into the URL, I can get a list of my threads.

Find All My Posts:
```

http://ubuntuforums.org/search.php?do=finduser&userid=223801&contenttype=vB&Forum_Post&showposts=1

```

Find All My Threads:
```

http://ubuntuforums.org/search.php?do=finduser&userid=&starteronly=1&contenttype=vBForum_Thread

```

It looks like from other pages (where Quick Links is on the left), it works fine.  It's just broken on the Search Results page (Quick Links on the right).

---

### Post by tgalati4 on 2014-12-11
It's working for me.  Perhaps clear your browser cache, close the tab, and open a new UbuntuForums tab, then log in.  Perhaps it's a bad load of the page.

---

### Post by coffeecat on 2014-12-11
Thanks for noticing this. It should be fixed now.

In fact it's not to do with the search page, but the tab in the navigation bar. Forum -> Quick Links -> Find all my threads was working, but Activity Page -> Quick Links -> Find all my threads was not. The advanced search page gives you the Activity Page navbar tab. Please test it now and see if it is working for you.

---

### Post by kpatz on 2014-12-11
Seems to be fixed now, thanks!

---

