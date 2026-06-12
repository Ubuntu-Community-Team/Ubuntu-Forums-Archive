---
title: "[SOLVED] Does Nautilus work with Devil's Pie?"
date: 2008-01-04
forum: Desktop Effects &amp; Customization
---

### Post by Tsi99 on 2008-01-04
I got Devil's to work with Thunderbird and Firefox.  But I can not seem to get it to work with Nautilus.

I am trying to send Nautilus to viewport 4 maximized with the following.  The file is labeled browser.ds

(if
(is (application_name) "Browser")
(begin
(set_viewport 4)
(maximize)
)
)

Any Ideas?

Thanks,
Matt

---

### Post by psyopper on 2008-01-04
seems that app name of "Browser" may be too generic? My experience with Devils Pie is limited (I have used it int he past though) so I can't recall if it supports a class rather than a name? 

A Nautilus browser window xprop's to WM_CLASS: "nautilus" "Nautilus" regardless of the contents of the window.

---

### Post by Tsi99 on 2008-01-05
Thanks,

Your suggestion sent me in the right direction.

I realized that my initial condition was trying to match the application name not window title.  I tried your suggestion by using 

(contains (window_class) "autilus") 

and other more strict variants (both contains and is) as a condition and my whole GUI was freezing up and acting weird.

I found using a window title condition work.

(if
(and
(contains (window_name) "matt")
(contains (window_name) "File")
(contains (window_name) "Browser")
)
(begin
(set_viewport 4)
(maximize)
)
)

A great Devil's Pie resource is [http://foosel.org/linux/devilspie](http://foosel.org/linux/devilspie)

---

