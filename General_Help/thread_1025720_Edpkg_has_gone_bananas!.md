---
title: "E:dpkg has gone bananas!"
date: 2008-12-30
forum: General Help
---

### Post by potion magique on 2008-12-30
Dear Sir or Madam,

Please forgive my contacting you directly. But I have been trying to log in and or register to use the forum, but without success on either count, and, as my problem is actually rather urgent, I felt it would be more apposite to contact a member of the Ubuntu community  directly, in the hope that one of you would be able to help, or put me in the direction of someone who could help!

A few days ago, as I was completing my usual weekly update for Ubuntu, my battery gave out very suddenly, and I was left unable to complete the update, nor to restart the update, indeed, unable to do any updating whatsoever!

These are the error messages I have received ever since:

E:dpkg was interrupted, you must manually run ‘dpkg  - configure  -a to correct the problem.

E: _cache->open() failed, please report.

No-one here has ever seen these messages, and so dare not try to help, in case they make things worse!

Is there any way, please, you could direct me to the right answer, using please the simplest and most clearly unambiguous of instructions!, or direct me to the appropriate person?

Many thanks indeed, and I very much look forward to hearing from you.

The reason there is urgency, by the way, is that I am due to be leaving for Prague on Sunday, and I’m going ot need the laptop for just about everything!

Thank you again, and again apologies, if this email has been directed inappropriately.

I'm not a complete duffer, having used Ubuntu quite happily for a couple of years on this old steam driven laptop, but this is beyond me - HELP!

Iain McGregor.

---

### Post by kelean on 2008-12-30
It tells you the answer.  Open a terminal Application>Accessories>terminal.
Once open type in the terminal.

```
sudo dpkg - configure -a
```

That should fix the errors and finish the needed updates.  If not please post the errors that it gives you.

Kelean

---

