---
title: "Force refresh unity in 14.04"
date: 2015-10-10
forum: Desktop Environments
---

### Post by Robin_Bertilsson on 2015-10-10
So.. I'm a web developer and was clicking around on [Behance]("http://www.behance.net"). Found the "[Stupendously Hot Charmander Concept]("https://www.behance.net/gallery/28804097/Ubuntu-1604-Stupendously-Hot-Charmander-concept")", i was so amazed and just had to do it!

So now we're here, I've created my theme or I'm trying to figure out the CSS structure etc, but found that fairly easy, but the question is..

How do I "restart/refresh" unity without logout/login.

```

$ unity (will force logout the user but does work)
$ unity --refresh (will do the same as unity)
$ unity-tweak-tool --unity-refresh (not working even tho I have UTT installed)

```

So.. How should i do this? i mean, is it any better way to do it or can i in some way (set up a script) perhaps(?) watching for file changes and then "refresh" the desktop? (as i do with gulpjs or grunt)..

Please help me, and I'm sorry if this post is in the wrong thread..

Thanks!
Robin.

---

### Post by mc4man on 2015-10-10
The current command would be 
setsid unity
but not always guaranteed to not cause a log out. On one install here it works as intended, the other install it always ends with a log out.

---

### Post by Robin_Bertilsson on 2015-10-10
Yeah, thanks. It did sign me out tho..

---

### Post by mc4man on 2015-10-10
Can't yet or ever figure out why it works without logout in some cases & doesn't in others.
I guess one thing to check could be to set up another user account, login to that account  & see what happens there.

---

