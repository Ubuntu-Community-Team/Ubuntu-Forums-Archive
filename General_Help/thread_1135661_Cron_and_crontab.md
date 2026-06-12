---
title: "Cron and crontab"
date: 2009-04-24
forum: General Help
---

### Post by desperateone on 2009-04-24
I'm having problems with using crontab. I got some file removal (simple rm -r stuff)  in there that runs every hour, and that one works alright, but I have also a general archiving command, in the form of ```
cat /home/me/ideas/* > /home/me/TOTAL
```, but it fails to work. Anyone knows what might be the cause?

---

### Post by paradigm2 on 2009-04-24
> **desperateone said:**
> I'm having problems with using crontab. I got some file removal (simple rm -r stuff)  in there that runs every hour, and that one works alright, but I have also a general archiving command, in the form of ```
cat /home/me/ideas/* > /home/me/TOTAL
```, but it fails to work. Anyone knows what might be the cause?

Does the command above work when done as the user the cron job is ran under?

post the output of:

```

crontab -l

```

---

### Post by desperateone on 2009-04-24
Yep, works alright when ran normally;

```
  00  *  *   *   *     rm -r /home/me/.thumbnails
  00  *  *   *   *     rm -r /home/me/.gqview/history
  00  0  *   *   *     history -c
  00  *  *   *   *     cat /home/me/ideas/* /home/me/ideas/x/* > /home/me/TOTAL
```

---

