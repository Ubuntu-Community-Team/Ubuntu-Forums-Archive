---
title: "terminal character encoding differences"
date: 2006-06-22
forum: Desktop Environments
---

### Post by fpeixoto on 2006-06-22
I run terminal applications from putty when I am away from my console using putty at work.

when I run certain applications the character encoding comes out all wrong.

at first I thought (wow, this app is awful), but then I did a test.  I created a new test user and ran the same app from that user, and it looks perfect.

I was looking around, and I saw that the issue might come from the fact that my initial user (at Ubuntu installation) might have been created using a different skeleton file than the new users.

now, I wonder, what should I modify to have my initial user have the same terminal settings as my new users (I've repeated the experiment with accounts for some coworkers using putty again)?

I'm attaching a screenshot of what my terminal ends up looking like in tMSNc.  This is after an interface refresh, but its gets much worse than that.  characters all over the place and such.

also, those **â **characters seperating the sections are supposed to be simple lines.

---

### Post by jvl on 2006-06-22
What is your locale setting? Do you use utf8? If yes, set the "character set translation to utf8"

see attached image:

The other way is:
$ export LC_ALL=C
and let putty use it's default encoding (ISO-8859-x)

national characters may look garbled.

---

### Post by fpeixoto on 2006-06-22
perfect!  that was it!

thanks.   I imagined it was something like that, but I didnt catch on.

---

