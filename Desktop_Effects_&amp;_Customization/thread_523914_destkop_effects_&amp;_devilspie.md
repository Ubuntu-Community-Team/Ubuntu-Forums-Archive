---
title: "destkop effects &amp; devilspie"
date: 2007-08-12
forum: Desktop Effects &amp; Customization
---

### Post by LucidParody on 2007-08-12
hi, just installed ubuntu 7.04.  i noticed that when i turn on desktop effects, i cannot force windows to always be on top, pin them to always be visible on all desktops, etc.  for example, devils pie pin will work perfectly when desktop effects is turned off but will not work at all when desktop effects is on.

any suggestions?

thanks

---

### Post by psyopper on 2007-08-12
I think I may know an answer but it would be helpful if you let us know exactly how you want/expect your Devilspied window to behave.

---

### Post by LucidParody on 2007-08-12
well, for example, here's my pidgin.ds file:

```

(if
    (and 
        (is (window_role) "conversation")
    )
    (begin
        (pin)
    )
)

```

i really don't think it's a problem with devilspie -- when i turn off desktop effects, devilspie works perfectly.  but with desktop effects enabled, devils pie does not work.

---

### Post by Incie83 on 2007-08-12
Try 'stick' instead of 'pin' and 'viewport' instead of 'workspace'

---

### Post by LucidParody on 2007-08-12
thanks, it works like a charm.  is there a reference for other changes with desktop effects?

---

### Post by Incie83 on 2007-08-12
Not that I know of... it's just a matter of common sense and using the [wiki]("http://foosel.org/linux/devilspie") for reference

---

