---
title: "Make terminals use transset at start"
date: 2007-11-20
forum: Desktop Effects &amp; Customization
---

### Post by PurposeOfReason on 2007-11-20
Is there a way to open a terminal with transset right when it starts? I'm trying to get urxvt to start with a slight transparency without that doesn't just copy the background.

---

### Post by PurposeOfReason on 2007-11-20
With a bit of looking I'm guessing that devilspie is my best bet so I tried

```

(if

(is (application_name) "URxvt")
(begin
  (spawn_async (str "transset-df -i " (window_xid) " .82" ) )
)

) 
```

but to no avail. Any help with this?

---

