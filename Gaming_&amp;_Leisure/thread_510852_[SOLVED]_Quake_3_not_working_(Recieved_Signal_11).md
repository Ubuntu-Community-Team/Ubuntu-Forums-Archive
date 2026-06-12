---
title: "[SOLVED] Quake 3 not working (Recieved Signal 11)"
date: 2007-07-27
forum: Gaming &amp; Leisure
---

### Post by captainwitherspoon on 2007-07-27
Hello, I'm trying to un quake 3. It works fine for a while but at seemingly random times it suddenly exits. When I run it in terminal I get a message that says "Received signal 11, exiting.."
I don't know why this is happening. I also tried nexuiz but it exits at random times as well with a different error message. I've searched many forums and can't find an answer, anyone out there?

---

### Post by dmn_clown on 2007-07-27
[http://www.sienet.hu/linux/sig11-FAQ.html](http://www.sienet.hu/linux/sig11-FAQ.html)

---

### Post by captainwitherspoon on 2007-07-27
Thanks a lot, I'll let you know if it works.

---

### Post by captainwitherspoon on 2007-07-29
I seem to have fixed that error. I had 40 conductor IDE cable attached  to my HD, I switched it out for 80 conductor. Now it sometimes exits with a "signal 6" error which only occurs when punkbuster is enabled. Unfortunately most servers use punkbuster so I'm still sort of screwed but not as bad as I was...

---

### Post by dmn_clown on 2007-07-29
> **captainwitherspoon said:**
> I seem to have fixed that error. I had 40 conductor IDE cable attached  to my HD, I switched it out for 80 conductor. Now it sometimes exits with a "signal 6" error which only occurs when punkbuster is enabled. Unfortunately most servers use punkbuster so I'm still sort of screwed but not as bad as I was...

Ahh punkbuster... there is nothing like being kicked off a server because the binary blob refuses to update correctly...

You are better off without it and if you are on a server with some one that is running a lagger or an aimbot ```
/callvote kick <username/id>
```

---

### Post by elvisthedj on 2007-08-14
If you're using the pbuptade script, make sure you look at the files in the pb folder.  I was getting a signal 6 and noticed the files were owned by root:root.  I changed them to root:games and everything works now.

---

