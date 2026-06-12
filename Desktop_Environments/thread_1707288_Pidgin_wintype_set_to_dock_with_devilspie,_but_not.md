---
title: "Pidgin wintype set to dock with devilspie, but not correctly working"
date: 2011-03-15
forum: Desktop Environments
---

### Post by LlamaBE on 2011-03-15
Hi,

First of all, let me mention I have upgraded to alpha version of Natty Narwhal, but I reverted my desktop to the classic (Gnome) desktop. This should not really matter for this problem though.

I have installed Pidgin and DevilsPie. I have set the following configuration for my Buddy List:

```
(if
    (and
        (is (application_name) "Pidgin")
        (is (window_name) "Buddy List")
    )
    (begin
    (undecorate)
    (stick)
    (geometry "264x1032-0+24")
    (skip_tasklist)
    (wintype "dock")
    )
)

```

What this does on my machine is put the contact list on the right hand border of the screen. I was hoping, that by using wintype dock, all other applications would maximize to the border of my pidgin buddy list. However, they seem to maximize to full width, with Pidgin having the "Always on top" attribute.

Is there any way to configure it so that maximizing other windows go up to the buddy list, but no further?

Thanks

---

