---
title: "Board keeps eating my newlines"
date: 2016-06-10
forum: Forum Feedback &amp; Help
---

### Post by &amp;KyT$0P# on 2016-06-10
When typing a post with newlines in it and clicking "Preview Post", the newlines got stripped out of the post.  Tried adding < b r  / > (with fewer spaces) on the end of the newlines, and that seemed to work, but then those were stripped out of the post on preview.  Short of hacking together a user script, is there a way to get newlines to stick?  (Maybe disabling HTML parsing in my posts, but I don't see how to do that?)  Thanks.

---

### Post by PaulW2U on 2016-06-11
Take a look at [this]("http://ubuntuforums.org/showthread.php?t=2316908") thread. You are not the first to post here with that problem which is usually easily solved.

Do you have yahooapis blocked?

---

### Post by &amp;KyT$0P# on 2016-06-11
Sorry, that thread didn't show up when searching.  I had tried unblocking yahooapis but it doesn't make any difference in my case :???: Since the issue is likely on my end I'll do some troubleshooting and post back if I get it working.

---

### Post by vasa1 on 2016-06-11
Which ad blockers or script blockers, if any, do you use? Could you disable them specifically for Ubuntu Forums and see if that makes a difference?

---

### Post by &amp;KyT$0P# on 2016-06-11
Actually, the problem in my case is accessing ubuntuforums.org over https.  Using plain http and it works (but is really slow compared to https). :o

Why does it break over https?  I'm not exactly comfortable sharing SSO information over plain http...

---

### Post by bapoumba on 2016-06-13
U1 SSO is over https. Once logged into the forums, identification is cookie based in your browser. We have been wanting to move UF to https for a long while but seems there are some issues not in our hands.

---

### Post by &amp;KyT$0P# on 2016-06-13
> U1 SSO is over https. Once logged into the forums, identification is cookie based in your browser.
Oh good, I was concerned my email address & username were getting constantly sent around together as I browse the board logged in.  Thanks bapoumba for the explanation!

---

