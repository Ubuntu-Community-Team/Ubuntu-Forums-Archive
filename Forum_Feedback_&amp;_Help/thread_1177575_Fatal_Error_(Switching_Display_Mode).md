---
title: "Fatal Error (Switching Display Mode)"
date: 2009-06-03
forum: Forum Feedback &amp; Help
---

### Post by trench.me on 2009-06-03
I tried to switch to "threaded view" and received the following fatal.```
Fatal error:  Allowed memory size of 805306368 bytes exhausted (tried to allocate 227313 bytes) in /srv/www.ubuntuforums.org/public_html/showthread.php on line 1272
```Figured somebody would probably like to know about that.[B] :)
[/B]

---

### Post by cariboo on 2009-06-03
I just tried it and it switched with no problems, maybe it was a temporary glitch. Why is there a poll that has nothing to do with the subject attached to this thread?

---

### Post by ubuntu-geek on 2009-06-03
Oh thats a good one I'll check it out. Perhaps the server was super busy or we have a mis-configuration.

---

### Post by ubuntu-geek on 2009-06-03
Looks like you just hit the forums at a really bad time when php memory was being exhausted for some reason. If it happens again please let us know.

---

### Post by trench.me on 2009-06-03
Makes sense. I'll let you know if anything else breaks. (I'd insert some kind of Electric Boogaloo reference here but I don't think Carib would be too happy.) 

**[[COLOR=#D40000][B]cariboo907**[/COLOR]]("http://ubuntuforums.org/member.php?u=77104") [/B]Re: Why the poll? - Just trying to add a bit of levity to the fatal report. And we all know that everything Fatal has to do with Scorpion.

---

### Post by trench.me on 2009-06-03
Ah, I've figured it out. It's completely recreatable. Go to [the bump thread]("http://ubuntuforums.org/showthread.php?t=520091&page=3974") and attempt to switch display modes. I believe you'll get the same error. No doubt it's because of the thread-size. [URL="http://ubuntuforums.org/showthread.php?t=520091&page=3974"]
[/URL]

---

### Post by ubuntu-geek on 2009-06-03
> **trench.me said:**
> Ah, I've figured it out. It's completely recreatable. Go to [the bump thread]("http://ubuntuforums.org/showthread.php?t=520091&page=3974") and attempt to switch display modes. I believe you'll get the same error. No doubt it's because of the thread-size. [URL="http://ubuntuforums.org/showthread.php?t=520091&page=3974"]
[/URL]
Ah yes, a unique thread .. perhaps its time to start another one.. :)

---

### Post by jenkinbr on 2009-06-04
> **ubuntu-geek said:**
> Ah yes, a unique thread .. perhaps its time to start another one.. :)
NO! :P

I like it the way it is! (just don't use threaded mode)

btw, I got the same error.  then again, it's not on my end (except for the fact that I've contributed 3,765 posts to that thread, but that's a different story :))

---

