---
title: "Pipe script output into environment variable..."
date: 2009-05-31
forum: General Help
---

### Post by Barriehie on 2009-05-31
So I'm using wget to return my IP but how do I pipe that into an environment variable???
```

wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]|.]//g'

```Thank You,
Barrie

---

### Post by shel-hall on 2009-05-31
> **Barriehie said:**
> So I'm using wget to return my IP but how do I pipe that into an environment variable???
```

wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]|.]//g'

```
You could try putting the command in back-ticks:
```

VAR=`wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]|.]//g'`
echo $VAR
```

-Shel

---

### Post by Barriehie on 2009-05-31
> **shel-hall said:**
> You could try putting the command in back-ticks:
```

VAR=`wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]|.]//g'`
echo $VAR
```-Shel

Thank You!  I wasn't getting very far with the front-ticks...  :p

Barrie

Edit:  I just googled and found at that enclosing in back-ticks is also like $(...) - good stuff!

---

