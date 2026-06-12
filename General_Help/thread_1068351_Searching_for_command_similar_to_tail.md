---
title: "Searching for command similar to tail"
date: 2009-02-12
forum: General Help
---

### Post by geo909 on 2009-02-12
Hello everybody,

I am searching for a command that outputs line n from the input.
This is similar to the tail command, but instead of having
the, say, 3 lines from the end, I want to have the third line from the end..

Do you know anything like that?

Thanks in advance!!

PS. I don't want to use tail in combination with grep

---

### Post by Slim Odds on 2009-02-12
```
tail -n 3 <logfile> | head -n 1
```

---

### Post by geo909 on 2009-02-12
I didn't think of that!
Thanks a lot!!

---

### Post by Slim Odds on 2009-02-12
> **geo909 said:**
> I didn't think of that!
Thanks a lot!!

You're welcome...

Chaining together all those cool little tools is what *nix is all about  :P

---

