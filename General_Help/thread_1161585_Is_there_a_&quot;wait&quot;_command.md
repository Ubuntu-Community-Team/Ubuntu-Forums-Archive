---
title: "Is there a &quot;wait&quot; command?"
date: 2009-05-16
forum: General Help
---

### Post by jakupl on 2009-05-16
I would like to do something like this:

```
(wait for 30 minutes) && pkill rhythmbox
```
I have usually used sudo shutdown -P 30, but the computer needs to stay turned on tonight.

---

### Post by damis648 on 2009-05-16
```
sleep 10; killall rhythmbox
```
Sleep is what you want (note that it uses time in seconds, so use parameters accordingly).

---

### Post by jakupl on 2009-05-16
> **damis648 said:**
> ```
sleep 10; killall rhythmbox
```
Sleep is what you want (note that it uses time in seconds, so use parameters accordingly).

Thankyou very much. That will come in handy.

---

