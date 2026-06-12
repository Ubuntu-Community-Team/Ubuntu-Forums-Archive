---
title: "Problem with edit after link"
date: 2013-04-13
forum: Forum Feedback &amp; Help
---

### Post by ibjsb4 on 2013-04-13
Is this a bug or just me?

[http://ubuntuforums.org/showthread.php?t=2134917&p=12601330&viewfull=1#post12601330](http://ubuntuforums.org/showthread.php?t=2134917&p=12601330&viewfull=1#post12601330)

---

### Post by coffeecat on 2013-04-13
The url BBCode tag prior to your edit hasn't been closed with a [noparse][/URL][/noparse] tag.  Here's your raw text together with the line preceding the edit:

> [noparse][URL="http://ubuntuforums.org/showthread.php?t=140920"]http://ubuntuforums.org/showthread.php?t=140920

Edit:  There should be a warning with deborphan.  It can remove necessary packages, use with caution.

Why can I not remove the link option when editing this post :confused:[/noparse]

The edit history shows that you added the link a second time and overwrote the [noparse][/URL][/noparse] tag when you edited the post. See if you can edit it now and close the url tag.

**EDIT**: all you should need to make a hyperlink of the URL in the first line is:

```
[noparse][http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)[/noparse]
```

---

### Post by ibjsb4 on 2013-04-13
Solved for now, see what happens next time I edit.  Thanks coffeecat

---

### Post by VinDSL on 2013-04-14
> **ibjsb4 said:**
> Is this a bug or just me?
In my experience, on VB forums et al, sometimes it's me (pilot error) and sometimes it's VB (possibly a bug).

I post a lot of code (here and elsewhere) and these posts tend to be long, and complex.

I always have to check the post AFTER it's submitted, to make sure VB didn't change the content when it was saved.

When I find errors in a submitted post, I try to use retrograde extrapolation (reverse-engineering, if you will) to figure out what happened.

Of course, I don't have the same tools available to me, as a mod/admin, but...

My gut feeling tells me that the problem is either some anomalies in the VB text editor(s), and/or BBCODE tag formatting,  and/or a corruption of the data when its written to the sql db.

Luckily, this sort of thing is fairly rare, but it does crop up from time_to_time in VB forums.

---

