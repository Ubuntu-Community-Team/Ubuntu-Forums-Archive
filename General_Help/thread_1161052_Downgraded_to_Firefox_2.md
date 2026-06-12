---
title: "Downgraded to Firefox 2??"
date: 2009-05-16
forum: General Help
---

### Post by K-Starz on 2009-05-16
I have been using Ubuntu 9.04 since I upgraded last week. I upgraded from 8.04.

All of a sudden, I noticed I had some weird issues with a web site. I went to make a bug report with them, and ... 

I'm using Firefox 2.0.0.12??  Also, all of my bookmarks are what they were  A YEAR AGO.

I'm an experienced Linux user (since 1999) and I have no idea what is going on here.

Why do I have FF 2 installed instead of 3.0.0.10 or whatever, and where did my old bookmarks come from??

---

### Post by K-Starz on 2009-05-16
Okay, I restarted my browser, and it's Firefox 3.0.10 again.

Can anyone explain this?

I really was using FF 2.0.0.12 there, evidenced in the Help > About menu. Websites were reacting differently. my bookmarks reverted to a year ago.

kev@ubuntu9sys:~$ firefox --version
Mozilla Firefox 3.0.10, Copyright (c) 1998 - 2009 mozilla.org

My normal FF gives this user agent
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.0.10) Gecko/2009042523 Ubuntu/9.04 (jaunty) Firefox/3.0.10


but I was leaving this in logs
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.12) Gecko/20080201 Firefox/2.0.0.12

Where did FF 2 come from? How is it still on my system?

'locate firefox' finds no other installation besides Firefox 3.

---

### Post by DeMus on 2009-05-16
> **K-Starz said:**
> I have been using Ubuntu 9.04 since I upgraded last week. I upgraded from 8.04.

All of a sudden, I noticed I had some weird issues with a web site. I went to make a bug report with them, and ... 

I'm using Firefox 2.0.0.12??  Also, all of my bookmarks are what they were  A YEAR AGO.

I'm an experienced Linux user (since 1999) and I have no idea what is going on here.

Why do I have FF 2 installed instead of 3.0.0.10 or whatever, and where did my old bookmarks come from??

You write you upgraded from 8.04. This would indicate you still have your same home folder with the .mozilla folder in it. Here is where the bookmarks and all other firefox settings are stored. That would explain for the old bookmarks.
Why you still have version 2 is something I am not sure of. Could it be it is also stored in this hidden folder? I don't know.

---

### Post by K-Starz on 2009-05-16
Thanks for taking a guess at this.

My .mozilla folder only has one profile, and it has indeed been in continuous use since I had FF2 installed.  Perhaps FF2 couldn't use the new FF3 bookmarks, and used an old backup file?

What I can't figure out is where the Firefox 2 binary came from since I upgraded to 3 like 6+ months ago.

---

### Post by DeMus on 2009-05-16
> **K-Starz said:**
> Thanks for taking a guess at this.

My .mozilla folder only has one profile, and it has indeed been in continuous use since I had FF2 installed.  Perhaps FF2 couldn't use the new FF3 bookmarks, and used an old backup file?

What I can't figure out is where the Firefox 2 binary came from since I upgraded to 3 like 6+ months ago.

Is there something of FF2 still on your disk somewhere? Maybe it was not removed when you upgraded from FF2 to FF3? I would say start looking around on your disk(s).
It's still strange that suddenly it appears again. Did you install an update of some kind, either FF itself or an addon maybe?

---

### Post by K-Starz on 2009-05-16
I've always allowed Firefox to be upgraded normally through aptitude or update-manager.

If I COULD run FF 2 on purpose, that would be nice for web site testing! Although few people use it these days.  I'll have to look around, the binary must be here somewhere...

---

### Post by K-Starz on 2009-05-17
So, there is no sign or indication of another version of Firefox anywhere on my system... this is all quite unexplained to me.

If anyone knows how Firefox 3 can suddenly turn into Firefox 2 (and it definitely did! The user agent in my web server logs proves this if nothing else) I'd be really interested in knowing.

---

