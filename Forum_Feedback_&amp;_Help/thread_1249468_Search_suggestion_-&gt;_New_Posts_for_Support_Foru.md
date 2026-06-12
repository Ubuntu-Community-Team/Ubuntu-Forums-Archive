---
title: "Search suggestion -&gt; New Posts for Support Forums only"
date: 2009-08-25
forum: Forum Feedback &amp; Help
---

### Post by DaithiF on 2009-08-25
Hi,
I've been on the forums just over a month.  Usually I'm looking for support threads that I can help on.  When clicking New Posts theres quite a bit of non-support, ie. discussion threads, polls, etc. that you have to filter out.  I haven't found a way (with Advanced Search) to do a New Posts search in just the Support Forums + Absolute Beginners sections.

Is there a way to do that?  

Or if not, may I put it forward as a suggestion for a pre-defined search under the 'Search' dropdown -- 'Get All New Posts (Support)'

thanks
D

---

### Post by DaithiF on 2009-08-27
i guess not a lot of interest in this then :)
just for the record, it turns out you can do it by passing a comma separated list of forum ids with an exclude parameter.
thus:
```
http://ubuntuforums.org/search.php?do=getnew&exclude=11,302,298,122
```will exclude any posts from:
11 The Community Cafe
302 Recurring Discussions
298 Community Cafe Games
122 The Fridge Discussions

and heres a greasemonkey script which replaces the New Posts link with a New Posts (support) equivalent
```
// ==UserScript==
// @name           UbuntuForumNewSearch
// @namespace      ubuntuforums.org
// @include        http://ubuntuforums.org/*
// ==/UserScript==
links = document.getElementsByTagName('a');
for ( var i = 0; i < links.length; i++) {
    a = links[i]
    if (a.href == 'http://ubuntuforums.org/search.php?do=getnew' && a.innerHTML == 'New Posts')
    {
        a.href = 'http://ubuntuforums.org/search.php?do=getnew&exclude=11,302,298,122'
        a.innerHTML = 'New Posts (support)'
    }
}

```

---

### Post by aesis05401 on 2009-08-27
That's interesting.  I wonder what the impact on cpu per session metric is if users start submitting their searches in that manner.

---

