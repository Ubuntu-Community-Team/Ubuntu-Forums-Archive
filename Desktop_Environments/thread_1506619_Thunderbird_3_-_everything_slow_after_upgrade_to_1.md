---
title: "Thunderbird 3 - everything slow after upgrade to 10.04"
date: 2010-06-10
forum: Desktop Environments
---

### Post by Mercedes300 on 2010-06-10
Hello,

After trolling the forums for an answer, and finding only partial answers, I decided to start my own thread.

I'm setup with my home directory mounted over an NFS. After the the upgrade to 10.04 and the included change to version 3 of thunderbird, everything in thunderbird is slow. From opening email, changing folders, deleting emails, all the way to closing the program, just takes a wile. So long that the cumulative effect is the program is virtually unusable.

I've turned off indexing. Is there anything else that I can do to speed things up? I don't need any more security features than 2.x.

I'm the ginny-pig for my office, so I would like to not have to change o another mail program. :)

System Specs:
Quad core AMD Phenom 9500 2.0 GHz
5 GB Memory
SATA2 HDD
Ubuntu 10.04
Thunderbird 3.0.4

Thanks,

Manny

---

### Post by nilarimogard on 2010-06-10
Have you tried 3.1 RC 2? The final version will be out in about a week or so.

---

### Post by jcoles on 2010-06-14
Thanks for starting this thread, Mercedes300. Are you using the 64-bit version of 10.04? That's what I have. I did a fresh install. 

I thought the sluggishness was because of indexing, so I left the program open and let it complete. But, the program is still extremely slow. 

The message preview can take a minute or more to display a message, although the first one is quick. Fortunately, if you double-click the message it opens quickly in a new tab. 

If a dialog box is slow to display, maximizing it usually restores normal response. 

Some menus drop down empty. Some parts of the window aren't drawn. This app is broken! Why waste peoples' time with it?

I had trouble composing and sending a message. I had to wait a minute or more for my typing to appear in the window! I hope the sending part worked. It was important.

10.04 LTS is not an alpha, or even a beta. Why include an app that is obviously not ready for prime time? 

We need reliable email.

---

### Post by XubuRoxMySox on 2010-06-14
My T-Bird 3 is slow too. Could it be that maybe the difference is that the new T-Bird defaults to IMAP instead of POP3? I always used POP3 in the previous T-Bird and it was plenty fast.

The SeaMonkey internet suite works just like the trusty old T-Bird 2 did. Nice 'n' fast, and still lets me compose e-mail with all the fancy formatting and animated gifs I like to insert in my messages. But the browser is kinda outdated. Still, it makes a pretty good substitute for buggy, slow T-Bird 3.

Okay for now,
Robin

---

### Post by Mercedes300 on 2010-07-08
I thought I would update this thread.

I am still experiencing slowness in Thunderbird 3. Lately I'm receiving two of every email, a new symptom. 

Thinking of work-arounds, does evolution import Thunderbird 3 cleanly? It would have to handle message filters, address books and sub-folders.

I'm coming up on having to upgrade my bosses computer, and email is a BIG deal.

Please help.

Thanks.

---

### Post by realflash on 2010-08-17
jcoles - I have the same problem as you.

On one desktop PC running 10.04 32-bit version, with an ATI card and the open source driver, Thunderbird is awful. On my laptop running 10.04 64-bit with an ATI card and the proprietary driver, Thunderbird is great.

On the affected computer, can you run the following command in a terminal, and then paste the output?

```
grep "LoadModule" /var/log/Xorg.0.log
```

That will show which display driver you are using. I am wondering if it is the same as mine.

---

