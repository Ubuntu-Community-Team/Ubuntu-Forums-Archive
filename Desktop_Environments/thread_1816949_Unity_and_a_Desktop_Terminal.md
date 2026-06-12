---
title: "Unity and a Desktop Terminal"
date: 2011-08-02
forum: Desktop Environments
---

### Post by robobart on 2011-08-02
Hi All,

I've recently upgraded to 11.04. I like unity alright, but I miss my desktop terminal I used to run under gnome. 

Here is what I was doing:

Using DevilsPie, I ran the script DesktopTerminal.ds:

<code>
(if
        (matches (window_name) "DesktopTerminal")
        (begin
                (undecorate)
                (maximize)
                (wintype "normal")
        )
)
</code>

Then I set my Terminal prefs so that the title wouldn't change etc and ran devils pie in the startup apps.

I also ran:

gnome-terminal --window-with-profile=DesktopTerminal

in the startup apps.

With unity, it just isn't as nice. Perhaps I need more restrictions in my devils pie code? Maybe I should do this a totally different way? 

If you are running a desktop terminal under unity, I'd like to hear from you!

---

### Post by wojox on 2011-08-03
Try this code:

```
(if
(matches (window_name) "DesktopTerminal")
(begin
(set_workspace 1)
(below)
(undecorate)
(skip_pager)
(skip_tasklist)
(wintype "utility")
(geometry "+0+0")
(geometry "1280x50")
)
)
```

```
gnome-terminal –window-with-profile= DesktopTerminal
```

---

