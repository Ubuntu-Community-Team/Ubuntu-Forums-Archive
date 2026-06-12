---
title: "Panel Question"
date: 2007-08-07
forum: Desktop Effects &amp; Customization
---

### Post by Bofur on 2007-08-07
I was just wondering if there were a way to completely autohide the panel because it still sticks out a little on autohide. Thanks.

---

### Post by dcotruta on 2007-08-07
The only way I've ever been able to do it is by setting the autohide on & using a 100 % transparency or a 1 pixel transparent image as the background.

---

### Post by dcotruta on 2007-08-07
Unless you also mean you want to get rid of the all the little button edges too.

In that case, open up gconf-editor, then navigate to apps --> panel --> toplevels --> top_panel_screen0 and edit the auto_hide_size to 0. That will make the panel dissapear completely (if you don't have transparency turned on [or a transparent background image set], you'll still get a 1 pixel line at the top of your screen).

Note that you can also edit the bottom panel from that same menu, and if you're working on multiple screens you'll probably have to edit the correct panel setting.

---

### Post by almalaci on 2007-12-06
I tried everything that's possible in the Panel properties settings but I still have a pixel height there when the panel is hidden. I wouldn't bother but it's always there and during movies and games it would be nicer not to see it.
Any other solutions?

---

### Post by victorbrca on 2007-12-06
> **almalaci said:**
> I tried everything that's possible in the Panel properties settings but I still have a pixel height there when the panel is hidden. I wouldn't bother but it's always there and during movies and games it would be nicer not to see it.
Any other solutions?

The instructions from "dcotruta" ddn't work for you?


Vic.

---

