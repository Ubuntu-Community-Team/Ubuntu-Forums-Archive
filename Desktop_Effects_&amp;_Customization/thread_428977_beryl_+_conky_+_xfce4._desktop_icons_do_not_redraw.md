---
title: "beryl + conky + xfce4. desktop icons do not redraw"
date: 2007-04-30
forum: Desktop Effects &amp; Customization
---

### Post by SpanishFranks on 2007-04-30
when I move icons around on the xfce4 desktop, they do not redraw properly and create a trail. Sometimes my screen can become filled with the images of old icons that are no longer there. No doubt conky is the cause, as this didn't happen before. I start conky 10 seconds after beryl loads so they play nicely together (sort of, it seems)

using:
xfce 4.4
beryl 0.2.0
conky 1.4.5

thanks

---

### Post by orb9220 on 2007-04-30
To get conky to ley my icons show on desktop I had to:

> # Create own window instead of using desktop (required in nautilus)
#own_window no
#own_window yes
#own_window_type override
#own_window_transparent 1

own_window yes
own_window_transparent yes
own_window_type root
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

---

### Post by rolf-c on 2007-04-30
Something to check, I have seen similar behavior when 'Desktop manager supports viewports' is enabled.

---

### Post by SpanishFranks on 2007-04-30
thanks for the responses, i've tried those things already but to no avail. heres a screenshot of the problem. 

Thanks

---

### Post by Shinobi326 on 2007-05-12
OMG I've spent hours researching why in the heck Beryl kept having this "trail" or redraw problem and all it was is that somewhere along the line I checked that "Desktop Manager Supports Viewports" which seemed to be the culprit.

Thank you so much for posting the screenshot and mentioning it!

---

