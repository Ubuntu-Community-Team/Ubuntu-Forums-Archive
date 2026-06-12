---
title: "Can not save game in Yamagi Quake II"
date: 2012-03-24
forum: Gaming &amp; Leisure
---

### Post by Rodney9 on 2012-03-24
When I try to save a game in Yamagi Quake II I get the following - ```
Couldn't write /home/rodney/.yq2/baseq2/save/current/server.ssv
```

How do I fix it so I can save ?

Rodney

---

### Post by winh8r on 2012-03-24
Did you try changing the permissions, to allow writing to the specified file?

---

### Post by Brebs on 2012-03-24
I would guess that you've been messing with your files as root, so the permissions are messed up.

First simple test:
touch /home/rodney/.yq2/baseq2/save/current/server.ssv

What error does that give?

This will probably fix it:
chown -R rodney: /home/rodney/.yq2

---

### Post by Rodney9 on 2012-03-24
> **Brebs said:**
> I would guess that you've been messing with your files as root, so the permissions are messed up.

First simple test:
touch /home/rodney/.yq2/baseq2/save/current/server.ssv

What error does that give?

This will probably fix it:
chown -R rodney: /home/rodney/.yq2

```
$ touch /home/rodney/.yq2/baseq2/save/current/server.ssv
touch: cannot touch `/home/rodney/.yq2/baseq2/save/current/server.ssv': Permission denied
```


```
chown: changing ownership of `/home/rodney/.yq2/baseq2/scrnshot': Operation not permitted
```

---

### Post by Brebs on 2012-03-24
Run that chown command as root.

---

### Post by Rodney9 on 2012-03-24
Thank You Brebs, that fixed it.

Rodney

---

