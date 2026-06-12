---
title: "glest crashes at game start"
date: 2007-07-28
forum: Gaming &amp; Leisure
---

### Post by darksidedude on 2007-07-28
I dont know if this has been posted before but, it will start fine ( looks good to play) but after the game loads the files before game starts it crashes and i have to restart X, no error screens or text  :confused:

---

### Post by darksidedude on 2007-08-13
anyone know what to do?

I have an nvidia 6200 if that helps

---

### Post by darkazurka on 2008-07-06
I also got an NV44A [GeForce 6200], with proprietary drivers. I'm sorry to know that this problem isn't covered by Ubuntu cause they are proprietary. Can I help nouveau?

---

### Post by kdorf on 2008-07-06
Run glest from the terminal, but redirect its output to some file so you can view errors even if X crashes.

```
glest > ~/error_log_name
```

Would redirect all of glest's output to a file called "error_log_name" in your home directory. See if that provides any helpful clues.

---

### Post by darkazurka on 2008-07-11
Thanks it's a useful command I've not thought of. I think it's practical to do that when someone encounters errors.

---

