---
title: "Is there a way to schedule Azureus to start/stop every day?"
date: 2009-01-10
forum: General Help
---

### Post by NEUR0M4NCER on 2009-01-10
I've read a little about cron, but it's all very old - is there a way to start Azureus, let's say, at 1am every day, and stop it at 9am?

---

### Post by sdennie on 2009-01-10
Sure.  Use crontab -e and add:

```

* 1 * * * DISPLAY=:0.0 azureus
* 9 * * * pkill azureus

```

---

### Post by NEUR0M4NCER on 2009-01-11
That seems... almost *too* simple! Thanks.

Just so's I know, if my g/f gets up in the middle of the night and turns it off for whatever reason girls do these things for, will it muck up the stop in the morning?

---

