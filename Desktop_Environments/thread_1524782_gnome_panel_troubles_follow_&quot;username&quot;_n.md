---
title: "gnome panel troubles follow &quot;username&quot; not /home/username"
date: 2010-07-05
forum: Desktop Environments
---

### Post by SaintDanBert on 2010-07-05
I have a user=XXXX with $HOME=/home/XXXX.

I create a new user=NNNN with $HOME=/home/NNNN.

If I do the following:
```

sudo -i
cd /home
mv  XXXX  TTTT
mv  NNNN  XXXX
mv  TTTT  NNNN

```

I expect that user=XXXX will login and see a fresh, default desktop.
I expect that user=NNNN will see whatever XXXX used to see.

If user=XXXX has gnome-panel troubles before I do this, I expect that
user=NNNN will now have those troubles.  Instead, the troubles follow
the username ... user=XXXX still has troubles even on the default desktop.

QUESTION: Does anyone have any ideas what is going on and how to fix things?

QUESTION: What could poison a "username" outside of the original contents of /home/username?

Stumped,
~~~ 0;-Dan

---

