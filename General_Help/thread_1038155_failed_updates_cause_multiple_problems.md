---
title: "failed updates cause multiple problems"
date: 2009-01-12
forum: General Help
---

### Post by bigO on 2009-01-12
I installed ubuntu for a friend on their request when they were tired of problems from their old os.  I installed the broadcom drivers after searching for a problem connecting the wireless, then began installing updates, from a wired connection.  About half way through the updates the laptop froze up. (I believe over heating to be the culprit and plan on telling him the fan needs to be cleaned or replaced.) I had to do a hard shutdown at this point and let it cool down.
  Upon starting the computer up however first thing I noticed is all of the icons are to a different theme, not really a big issue but it peaked my curiosity. It appears to be stuck in Clear looks or glossy no matter what I choose.  A bigger problem however I can not launch most programs, so far only two things I have found to work are 1) terminal, 2) pidgin.
  I'm leaning toward telling him I won't do anything more until the over heating issue is resolved and then to a clean install at that point but any insights or opinions would be helpful.

---

### Post by bigO on 2009-01-12
O.K. I am writing this incase someone has the some issue and searches the forum. Basically the problem got fixed when I re-broke my habit formed from prior os use.  I have used linux for about a year now and still haven't broken all of my old habits. relying on GUI too much.

in terminal I did this.

```
sudo dpkg --configure -a
```

then
```
sudo apt-get update
```

and finally
```
sudo apt-get upgrade
```

followed by a reboot and everything is as it should be.
Except for his little over heating problem.

---

