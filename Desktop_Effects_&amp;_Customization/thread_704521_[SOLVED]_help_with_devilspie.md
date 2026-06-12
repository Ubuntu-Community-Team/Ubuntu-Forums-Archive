---
title: "[SOLVED] help with devilspie"
date: 2008-02-22
forum: Desktop Effects &amp; Customization
---

### Post by rob1984 on 2008-02-22
can anybody help me with devilspie?

i'm trying to embed a terminal on my desktop. i've followed the tutorial and all i get is a regular terminal window. 

my config file looks like this:

(if
(matches (window_name) &#8220;DesktopConsole&#8221;)
(begin
(set_workspace 1)
(below)
(undecorate)
(skip_pager)
(skip_tasklist)
(wintype &#8220;utility&#8221;)
(geometry &#8220;+50+50&#8243;)
(geometry &#8220;924×668&#8243;)
)
)

---

### Post by rob1984 on 2008-02-23
solution: type the config file manually.  
don't copy and paste from the net.

---

