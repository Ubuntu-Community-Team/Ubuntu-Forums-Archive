---
title: "[gnome] devilspie didnt work for gnome-terminal"
date: 2009-06-28
forum: Desktop Environments
---

### Post by grzeslaw on 2009-06-28
Hello

I used devilspie to customise locations and sizes for my applications. But unfortunetely for gnome-terminal it didn't work.

Here's my config:
```

(if (is  (application_name) "gnome-terminal") 
(begin
(set_viewport 1)
(center)
)
)

```

For comp for the thunderbird with the similar config works fine:
```

(if
(is (application_name) "Thunderbird")
(begin
(set_viewport 4)
(maximize)
)
)

```

I tried replacing the application_name with window_class but it didn't solve problem.

Where could be the problem?

---

