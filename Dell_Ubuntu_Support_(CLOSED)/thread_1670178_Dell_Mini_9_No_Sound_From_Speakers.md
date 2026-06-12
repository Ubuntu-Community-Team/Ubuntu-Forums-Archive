---
title: "Dell Mini 9 No Sound From Speakers"
date: 2011-01-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by zanderone on 2011-01-18
Hello

I have a Dell Mini 9 running 8.04 hardy heron which tells me it is updated

I get sound from headphones but not from the internal speakers. All volumes (master and speaker) are up and not muted.

The forum review I have done gives me the feeling this might be a hardware problem.

Any other options??  If it is hardware is there anything I can do?

Thanks for the help!

Alex

---

### Post by mikewhatever on 2011-01-18
Here is a similar problem solved with a Dell mini 9.
[http://ubuntuforums.org/showthread.php?t=1669056](http://ubuntuforums.org/showthread.php?t=1669056)

---

### Post by zanderone on 2011-01-18
Thanks Mike!
but...
That link doesnt really address my problem, that guy was just making a silly mistake.

Can anyone else weigh in on any possible fixes? Even hardware fix advice would be appreciated, Ill pop this baby open.

Thanks again.

---

### Post by davepoth on 2011-01-18
Long, long time since I had this issue. It's got something to do with the "special" Dell respositories which don't update anywhere near as regularly or completely as the Canonical ones. There was something missing, and I recall I had to upgrade I think ALSA to make it work properly.

In the end I was having too many issues with the Dellbuntu and so I upgraded it to the main Ubuntu trunk version on my Mini 9. So long as you make a full backup of your "home" directory the process is pretty much foolproof.

-Edit-

At least it solved my problem. It may be that you have a different one. If it is hardware it's quite an easy thing to take to pieces.

---

