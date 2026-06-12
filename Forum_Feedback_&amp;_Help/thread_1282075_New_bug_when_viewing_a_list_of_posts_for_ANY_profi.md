---
title: "New bug when viewing a list of posts for ANY profile"
date: 2009-10-03
forum: Forum Feedback &amp; Help
---

### Post by MaxIBoy on 2009-10-03
This has started in the last couple of days.

Steps to reproduce:

[LIST=1]
[*]Go to your own profile (or someone else's,) click "statistics"
[*]Click "find all posts by [USER]"
[*]Even if you haven't made a search recently, you still get the "This forum requires that you wait 15 seconds  between searches. Please try again in *n* seconds."
message.
[/LIST]

This is not major but kinda irritating.

---

### Post by cariboo on 2009-10-03
I've just done several searches of the forums, saw your post and checked your profile, then clicked Statistics-->Find all posts by MaxIBoy, I didn't see any message saying I had to wait for 15 seconds.

---

### Post by SoftwareExplorer on 2009-10-04
Seem to happen to me, at least when I search for all my posts. Does it still do it to you? What happens after you wait how many ever seconds it says you have to wait?

---

### Post by Tipped OuT on 2009-10-04
> **cariboo907 said:**
> ... I didn't see any message saying i had to wait for 15 seconds.

+1

---

### Post by MaxIBoy on 2009-10-04
It still happens to me viewing ANY profile. After I wait the time, I can view the results, go to other pages of the results, etc. If I click on the "view all posts by [USER]" option even after waiting more than 15 seconds, I still need to wait the time again. In a different tab or the same tab, doesn't matter.


I imagine some variable like "timeWaited" defaults to zero, so the code is dutifully making me wait until it equals 15.

---

