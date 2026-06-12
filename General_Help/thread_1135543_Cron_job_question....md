---
title: "Cron job question..."
date: 2009-04-24
forum: General Help
---

### Post by bmturney on 2009-04-24
I've just taken over administering a linux box, and i'm trying to straighten out some messes... one of the messes that I have are cron jobs... I have a couple of questions just to make sure I'm clear about this...

I have a couple of cron jobs setup like this

*  18  * * * /home/user/script1
*  *  * * * /home/user/script2


Please correct me if I'm wrong on this, but the first entry looks like it runs script1 ever minute during the 6:00 PM hour every day.

The second entry looks like it runs script2 every minute of every hour of every day... 

Am I reading these correctly?

---

### Post by joeyknuccione on 2009-04-24
Type in a terminal:

```

man cron

```
That's the best I can offer, but I feel confident it'll square ya away.

---

### Post by IsstanarLW on 2009-04-24
minute hour day month weekday command

So yes you're reading it correct.

---

### Post by paradigm2 on 2009-04-24
> **bmturney said:**
> I've just taken over administering a linux box, and i'm trying to straighten out some messes... one of the messes that I have are cron jobs... I have a couple of questions just to make sure I'm clear about this...

I have a couple of cron jobs setup like this

*  18  * * * /home/user/script1
*  *  * * * /home/user/script2


Please correct me if I'm wrong on this, but the first entry looks like it runs script1 ever minute during the 6:00 PM hour every day.

The second entry looks like it runs script2 every minute of every hour of every day... 

Am I reading these correctly?

Yes that's what it looks like.

I would look at the scripts and see what they are doing.  It sounds like this might be a server?  If so perhaps these perform some sort of watchdog type function checking to make sure a service is working and if not restarts it.  I dunno.  Definitely check what the scripts do.

---

### Post by bmturney on 2009-04-24
You guys rock... thanks for the help... I've already checked what these scripts do... its ridiculous... if I told you, you would probably die laughing... so I'll spare you... 

Thanks again.

---

