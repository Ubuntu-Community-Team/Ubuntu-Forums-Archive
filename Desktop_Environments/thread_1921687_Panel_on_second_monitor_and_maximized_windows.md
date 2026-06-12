---
title: "Panel on second monitor and maximized windows"
date: 2012-02-07
forum: Desktop Environments
---

### Post by Hety on 2012-02-07
Hello everyone,

i recently switched from ubuntu to xubuntu (hello, Unity! or rather Bye!) and everything is good beyond expectations, except one thing:

i created a panel on my second monitor to use it as a holder for windows buttons for it. It works perfectly, but maximized windows on second monitor ignore it completely and go under it. Its located at the left border of screen (i moved panel 1 to left border also on main monitor) and has exactly the same settings as panel1. Panel 1 is working as intended - new panel is not. 

Any ideas on the matter?

I'm using Xubuntu 11.10.

Upd: placing panel at the right border of the second monitor works fine. Windows see it and don't draw under it.

---

### Post by zhvihti on 2012-05-03
Strange, I'm running Xubuntu 12.04 (used to be 11.10) and don't have this issue - maximized windows on the second monitor stop at the panel, just like on the primary. Maybe try recreating the panel.

---

### Post by Janiporo on 2012-07-23
I got rid of ubuntu after 10.04, and setting up Xubuntu 12.04 for three reasons:
1.unity
2.second display does not work properly with nvidia card
3.unity

It just sucks SO bad.

Anyhow, this might work:

Try to use Compiz config manager, and set on "place windows", in settings / put method to "intelligent". This is how I got rid of that problem.

Another hand I can not get rid of the lover panel, and duplicate the upper panel.

Using cairo-dock at bottom, and xubuntu own panel at the top (The one that shows time and running programs)

Could you Lighten me how I get rid of lower panel and duplicate upper panel to second monitor/display?

This starts cairo on second display:
```
DISPLAY=:0.1 cairo-dock &
```
But what is the command to start another upper xubuntu dock, or how do I do it? O_o
(Not sure is "&" needed, do not remember how it got there)

I would use Cairo dock to display running programs, but it does not show them all, and some other problems :(

Just trying to google it.

---

### Post by cheri703 on 2013-01-25
> **Hety said:**
> Hello everyone,

i recently switched from ubuntu to xubuntu (hello, Unity! or rather Bye!) and everything is good beyond expectations, except one thing:

i created a panel on my second monitor to use it as a holder for windows buttons for it. It works perfectly, but maximized windows on second monitor ignore it completely and go under it. Its located at the left border of screen (i moved panel 1 to left border also on main monitor) and has exactly the same settings as panel1. Panel 1 is working as intended - new panel is not. 

Any ideas on the matter?

I'm using Xubuntu 11.10.

Upd: placing panel at the right border of the second monitor works fine. Windows see it and don't draw under it.


I just installed Xubuntu 12.10 and xfce 4.12 (I couldn't get non-mirrored dual monitors working without it), and I'm having the exact same behavior. Specifically, any vertical panel that is along the "seam" between the two monitors. When I maximize a window, it goes underneath the panel.

I think it is something to do with those panels not being recognized as "screen edge" panels, it treats them as though they're floating, which is why other vertical panels along the outside edges behave as expected. I am not sure if there's a fix or if I should file a bug against something.

If I should start a new topic, I'm happy to, but I figured since it's the same issue I'd revive this one. Thanks!

---

