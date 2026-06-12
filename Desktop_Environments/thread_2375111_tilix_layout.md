---
title: "tilix layout"
date: 2017-10-22
forum: Desktop Environments
---

### Post by zkab on 2017-10-22
I have installed tilix 1.6.4 in my xfce desktop.
I don't understand the session layout of tilix ... I have created 3 layouts (chk attachment) and saved the session ... but when I start tilix with that session name I only get the first one

---

### Post by again? on 2017-10-23
Wouldn't you need to save a different session in each tilix window and then start all 3.
eg
```
tilix -s session1
tilix -s session2
tilix -s session3
```

---

### Post by zkab on 2017-10-23
OK - what I did was ...
tilix -s session1 -s session2 -s session3
and it worked.
But I haven't figured out how I can get session1 to be displayed first ... now session3 pop-up first.

---

