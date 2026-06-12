---
title: "Forum stats on front page.."
date: 2006-11-10
forum: Forum Feedback &amp; Help
---

### Post by adam.tropics on 2006-11-10
Would there be any chance of bringing back an online user count (I may have gone blind but didn't see it). To justify, for users **not** in North America, it is pretty helpful to know if we are posting to any live bodies or not! As if the issue is important, we need to choose our timing for maximum response. Silly I know, but a very real issue since not enough people yet use the 'unanswered posts' search I think.

---

### Post by PriceChild on 2006-11-10
This was disabled to help with the server hits for the Edgy release.

You may still find it at [http://ubuntuforums.org/online.php](http://ubuntuforums.org/online.php)

There's normally at least 800 people online even at the quietest times.

---

### Post by adam.tropics on 2006-11-10
Thanks, and the stat is useful to know, though to make the point, it's the members you want as opposed to guests, as they 'tend' to be more interested! Anyway, no matter, and thanks for the link. Just quickly though, does something so trivial really inflict so much pressure on the server?

---

### Post by PriceChild on 2006-11-10
> **adam.tropics said:**
> Just quickly though, does something so trivial really inflict so much pressure on the server?At the busiest we were regularly experiencing about 3000 users.

Imagine every user hits the front page every 5 minutes, that's 600 every minute, 10 every second. - pure guesswork, but now every time that frontpage is brought up... there's an extra call to the database server asking it to count everyone online and report back the number as well as give you all the names of users online.

This is on top of another few hundred page requests every second as users browse threads, with extra calls on those that we've removed (how many people browsing subforum) and it really starts to add up.

Pricey

---

### Post by adam.tropics on 2006-11-10
Ok, all accepted and thanks for your time. But on a sidenote, the link you gave me is very helpful, but if the number of database calls is an issue, how come they have included a page refresh function that calls the stats again every minute or so! Please don't change it btw, I like that bit!

---

### Post by PriceChild on 2006-11-10
> **adam.tropics said:**
> But on a sidenote, the link you gave me is very helpful, but if the number of database calls is an issue, how come they have included a page refresh function that calls the stats again every minute or so!Cuz you're probably the only one doing it so it doesn't count for much ;)

Thanks for your understanding :)

If the forums quieten down, you never know UG might decide to put those features back on.

By the way, last time i asked, the database alone was over 3Gb, as opposed to just 1.5Gb 6 months ago. - Ubungu-geek's done A LOT of tuning :D

---

