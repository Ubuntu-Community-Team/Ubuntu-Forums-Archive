---
title: "Multiple terminals with devilspie"
date: 2007-09-14
forum: Desktop Effects &amp; Customization
---

### Post by riaal on 2007-09-14
Hi!

I have some problems getting more then one terminal pinned to my desktop. I want them on the same workspace.

I have made two Gnome-terminal-profiles: DesktopConsole and DesktopConsole1

And here is my devilspie config (DesktopConsole.ds)

```
(begin
        (if
                (matches (window_name) "DesktopConsole")
                (begin
                        (set_workspace 1)
                        (below)
                        (undecorate)
                        (skip_pager)
                        (skip_tasklist)
                        (wintype "utility")
                        (geometry "+50+50")
                        (geometry "700x1000")
                )
        )

        (if
                (matches (window_name) "DesktopConsole1")
                (begin
                        (set_workspace 1)
                        (below)
                        (undecorate)
                        (skip_pager)
                        (skip_tasklist)
                        (wintype "utility")
                        (geometry "+800+50")
                        (geometry "700x700")
                )
        )
)
```

Only one of them (first one) shows. Anyone have a clue how to fix this?

Tacks!

/Richard

---

