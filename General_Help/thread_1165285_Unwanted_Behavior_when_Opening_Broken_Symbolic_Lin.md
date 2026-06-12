---
title: "Unwanted Behavior when Opening Broken Symbolic Link"
date: 2009-05-20
forum: General Help
---

### Post by Bender2k14 on 2009-05-20
When I open a broken symbolic link, a somewhat expected window appears first:
[IMG]http://i41.tinypic.com/1zyfudj.jpg[/IMG]

Then, a few seconds later, this window appears:
[IMG]http://i42.tinypic.com/2vjr6mg.png[/IMG]

I do not think that the second window should appear.  The reason that the opening the "broken_link" file seems unresponsive is because it is waiting for a human response.

Also, I cannot even click the button in the second window.  I have to first select an option from the first window.

Anyone else think that this is a bug?

---

### Post by Bender2k14 on 2009-05-22
*cough* bump *cough*

---

### Post by ibuclaw on 2009-05-22
I was about to say that I couldn't reproduce this, but then I waited about 5 seconds, and yes, it did appear.

I wouldn't say it is a bug, just a small clash between two features.

The functions that this happens in is **report_broken_symbolic_link()** (dialogue box for clicked broken links) and **timed_wait_callback()** (dialogue box for when a file is taking more than 5 seconds to open - ie: large files).

I guess a simple option would be to cancel the timed_wait_callback timer...

If you think it's a problem, report a bug:

```
ubuntu-bug nautilus
```
Also, make sure that it hasn't already been reported.

Regards
Iain

---

### Post by ibuclaw on 2009-05-22
For your information, I have made a possible fix (in 16 minutes, not bad).

Just about to test it now.

---

### Post by Bender2k14 on 2009-05-22
Ok, sweet.  I was going to post a bug report.  I will wait a bit longer for you to do some more work and testing.

---

### Post by ibuclaw on 2009-05-22
I would personally just report a bug.

It's better if more eyes can see it ;)

Regards
Iain

---

### Post by Bender2k14 on 2009-05-22
[QUOTE=tinivole]I wouldn't say it is a bug, just a small clash between two features.[/QUOTE]

Yea, I do not think that this is really a bug either.  That is why I used the phrase "unwanted behavior" instead of bug (though I did add "bug" as a tag).

There is already a [bug report in Launchpad]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/263266") and they recently opened a [Bugzilla bug report]("http://bugzilla.gnome.org/show_bug.cgi?id=579165") for Gnome.

---

