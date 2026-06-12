---
title: "Docking Pidgin or changing the maximized window size"
date: 2009-05-02
forum: Desktop Environments
---

### Post by K. Hendrik on 2009-05-02
Hi,
i really would like to dock my pidgin to the right desktop side so that maximized windows dont hide it.
I know this has been discussed earlier but with no sattisfying result.
I know about devilspie and I already use it to stick pidgin on the right of my desktop, my current devilspie file looks like this:
```

(if
    (and 
        (is (application_name) "Pidgin")
        (is (window_name) "Buddy-Liste")
    )
    (begin
    (undecorate)
    (stick)
    (geometry "214x1032-0+24")
    (skip_tasklist)
    )
)

```

the problem is when I maximize a window it still covers the buddy-list up, I know i could use allways on top but I don't want the buddylist to cover the maximized window either, so is there any possibillity to reduce the size that a maximized window would use or do you know any other way to dock pidgin like it can in windows.

---

### Post by K. Hendrik on 2009-05-02
bump

---

### Post by K. Hendrik on 2009-05-04
another bump, does nobody know aything about this?

---

