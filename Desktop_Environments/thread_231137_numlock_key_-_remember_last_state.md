---
title: "numlock key - remember last state"
date: 2006-08-07
forum: Desktop Environments
---

### Post by Darrin on 2006-08-07
I read somewhere awhile back that the next version of ubuntu would have an option that would remember the last state of the numlock key. Has this been confirmed?

---

### Post by aysiu on 2006-08-07
"[N]ext version" meaning Edgy Eft? I don't know about that.

But Dapper doesn't have that built in. You can add it by [enabling extra repositories](http://www.psychocats.net/ubuntu/sources) and then installing *numlockx*: ```
sudo aptitude update
sudo aptitude install numlockx
```

---

### Post by Darrin on 2006-08-07
I dont know if it was suppose to be edgy or not. But this will work. Thanks

---

### Post by Anduu on 2006-08-07
Just a note...numlockx will not remember the last state...it either sets it to on or off.

---

