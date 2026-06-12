---
title: "Panel transparency"
date: 2009-04-25
forum: Desktop Environments
---

### Post by Mister LinOx on 2009-04-25
Okay. When I use the Glossy theme, everything on the bar is transparent. Not the icons and text, but I think you understand.
  Anyway, I recently downloaded the GTK 2.x theme Bluesy, and since then, certain spots on the panels are not transparent. For example: The windows list buttons used to be transparent. Not now. The clock and notification area used to be. Not now. There's a few others.
  So, do any of you know what caused this and/or how to fix it?

By the way, the attachments are below.

---

### Post by Mister LinOx on 2009-04-25
Sorry, but bump.

---

### Post by Mister LinOx on 2009-04-25
Wow. I'm guessing this hasn't happened before? Oh well. I can wait for someone to find a way.

---

### Post by mcduck on 2009-04-26
The problem is the GTK theme you downloaded. It defines bakground pictures/colors for those panel widgets, and this overrides what ever settings you do in the panel configuration.

There are only two ways to solve the problem, use some other GTK theme, or edit the theme and remove every section that sets a background for panel widgets.

(edit: by the way, please don't bump your threads that much. Once in a day, if you *really* have to. People will answer your questions as soon as somebody who knows the answer reads it. Bumping doesn't really help.)

---

### Post by danielgc.com on 2009-04-30
so, there isn't a way to apply some level of transparency to the theme? thx for your reply, I was wondering the same thing

---

