---
title: "Can't post new thread"
date: 2021-03-15
forum: Forum Feedback &amp; Help
---

### Post by hornetster on 2021-03-15
Trying to post new thread in Multimedia ([https://ubuntuforums.org/forumdisplay.php?f=334](https://ubuntuforums.org/forumdisplay.php?f=334)) and getting a Forbidden message: 

```
Forbidden
You don't have permission to access /newthread.php on this server.

Apache/2.4.7 (Ubuntu) Server at ubuntuforums.org Port 443
```

URL: [https://ubuntuforums.org/newthread.php?do=postthread&f=334](https://ubuntuforums.org/newthread.php?do=postthread&f=334)

Obviously can post here, though....

---

### Post by coffeecat on 2021-03-15
Ever since Canonical IS hardened the server after a serious hack some years ago, the vBulletin software occasionally and unpredictably does kooky things like this, and adds insult to injury by displaying that totally unhelpful forbidden message. Canonical IS did some fine tuning at the time, but I believe this is as good as it is likely to get without compromising security. I'm being deliberately vague about details for obvious reasons. Be assured, I feel for you. Sometimes it tells me that I don’t have permission to move a thread, or some other thing that forum staff are meant to do. Seriously?

Anyway, in your case I suspect that a particular string in perhaps some code or terminal output is being wrongly interpreted as malicious, or perhaps you've exceeded a certain character limit - that sometimes causes the error. If you tried to post the same thing in this sub -forum, I'm sure you'll get the same forbidden message.

What sort of thing are you trying to post? Perhaps the use of Ubuntu pastebin with a link would be a workaround.

---

### Post by hornetster on 2021-04-02
I am CONSTANTLY getting this message.
Don't seem to be able to post anything in the forums (except for maybe here....)
What's the fix?

---

### Post by hornetster on 2021-04-02
The thread I am trying to post is the attached text.

Why the problem??

---

### Post by coffeecat on 2021-04-02
I've found the problem. As I guessed it was around the http bit of your text. Post this:

> HTTP

And/or post this:

> /1.1

And the server is as happy as Larry. But if I put the two together, I get:

> Forbidden

You don't have permission to access /newreply.php on this server.
Apache/2.4.7 (Ubuntu) Server at ubuntuforums.org Port 443

Just like you. I can't remember the details now, but I do remember that Canonical IS had to do a lot of fine tuning of the security hardening to try to minimise spurious errors. Put those two strings together and the server has a fit of the vapours. I'll try raising a ticket to see if this particular string could be tolerated, but please don't hold your breath. In the meantime, I suggest you get creative with your post. I think just the "404 not found" is the important bit, and that at least will not upset the server.

---

### Post by hornetster on 2021-04-02
Thanks, Done!!

---

