---
title: "Adept problem (Please reply!)"
date: 2006-08-19
forum: Desktop Environments
---

### Post by Zach1188 on 2006-08-19
When I go to K menu > System > Adept, it asks for my password, so I enter it. A moment later, I get this error message:

[img]http://img243.imageshack.us/img243/7097/snapshot1bo1.png[/img]

I have been searching google all day, nothing has helped.

This happened when I was trying to install "sun-java5-jre". It was installing fine, then it hung at 28%. So I closed adept, and now adept is completely screwed over.

If I remember right, it hung at 28% of the EULA.

---

### Post by taurus on 2006-08-19
Open a terminal and see if there is another copy running in the background!

```
ps -A
```
And if there is, kill it with

```
kill -9 1234
(where 1234 is the PID, the number on the first column when you run "ps -A"...)

```

---

### Post by Zach1188 on 2006-08-19
What would it show up as (or I can post the entire list if you want)?

---

### Post by taurus on 2006-08-19
If you are not sure how to read it or how to kill it, yes, post the whole output of "ps -A" from a prompt then.

---

### Post by Zach1188 on 2006-08-19
Nevermind. Just now on my **FOURTH HOUR** searching on google, I found [http://kubuntuforums.net/forums/index.php?topic=8001](http://kubuntuforums.net/forums/index.php?topic=8001)

---

