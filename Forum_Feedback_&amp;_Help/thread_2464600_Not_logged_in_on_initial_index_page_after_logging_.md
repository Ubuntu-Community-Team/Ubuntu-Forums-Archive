---
title: "Not logged in on initial index page after logging in through SSO"
date: 2021-07-06
forum: Forum Feedback &amp; Help
---

### Post by &amp;KyT$0P# on 2021-07-06
When I log in through SSO, it redirects me to the "Thank you for logging in" page, then back to the index page.  But then I'm not logged in until I click a link on the forum?  Not even Ctrl-Shift-R or trying again to "Login with SSO" gets me logged in on the initial index page.

This only started today.  I'm pretty sure I didn't change anything in my browser between when this worked and now.

Is this just me or is anyone else noticing this?

---

### Post by Irihapeti on 2021-07-06
A few others have noticed this as well. Probably it's a consequence of the forums having been upgraded.

---

### Post by rsteinmetz70112 on 2021-07-06
If you go into one of the sub forums it should show you logged in, at least mine does.

---

### Post by Doug S on 2021-07-06
> **rsteinmetz70112 said:**
> If you go into one of the sub forums it should show you logged in, at least mine does.Same thing here. And after logging in a few times, I tried just going to a sub-forum and it was O.K.

---

### Post by Cavsfan on 2021-07-06
> **rsteinmetz70112 said:**
> If you go into one of the sub forums it should show you logged in, at least mine does.

Same thing here. I logged in twice before I seen this tread.

---

### Post by &amp;KyT$0P# on 2021-07-07
Thanks all for the replies and for confirming this.

Maybe I wasn't specific enough when I wrote "a link on the forum".  Yes clicking a link to a sub-forum or post does get me logged in.  As does clicking the Ubuntu Forums logo in the upper left or the "Forum" link back to the index page, even though I am already on the index page and as said reloading bypassing cache doesn't help.  I didn't test other links.

---

### Post by sajoupa on 2021-07-07
Indeed this was a consequence of the maintenance yesterday.
The forum  was moved to new servers, which included a more recent version of  apache2. This introduced a regression, where the home page was cached  and didn't show that the user was logged in. (Refreshing, or displaying  any page on the forum, would work around it)
It is now fixed. Sorry for the inconvenience.

--
sajoupa
Canonical IS

---

### Post by rsteinmetz70112 on 2021-07-07
It's now fixed but while it was going on refreshing or reloading the home page didn't fix the issue for me nor did opening another page inside the forum.

---

### Post by &amp;KyT$0P# on 2021-07-07
> **sajoupa said:**
> Indeed this was a consequence of the maintenance yesterday.
The forum  was moved to new servers, which included a more recent version of  apache2. This introduced a regression, where the home page was cached  and didn't show that the user was logged in. (Refreshing, or displaying  any page on the forum, would work around it)
It is now fixed. Sorry for the inconvenience.

--
sajoupa
Canonical IS

Confirmed fixed, thanks sajoupa! :KS

---

### Post by TheFu on 2021-07-07
I saw this too.

Also seeing 
> Forbidden

You don't have permission to access this resource.
Apache/2.4.29 (Ubuntu) Server at ubuntuforums.org Port 443 
when replying to posts in threads that normally would work.  Simple replies work, but if I use list-tags, forbidden.  It isn't related to Adv or normal reply. It seems tied to the tags used.

---

### Post by TheFu on 2021-07-07
Appears that the size limit on posts is the issue.
I split 2 posts up here: [https://ubuntuforums.org/showthread.php?t=2464224&p=14047413#post14047413](https://ubuntuforums.org/showthread.php?t=2464224&p=14047413#post14047413)
Together, the Forbidden permissions happened. The exact same posts, split into 2 posts by moving 1 paragraph into a different post seems to have solved it. Odd.

---

