---
title: "new monitor, now desktop problems"
date: 2008-12-28
forum: Desktop Environments
---

### Post by dcottingham on 2008-12-28
Just got a ViewSonic VA703b, and swapped it in as a new external monitor on my laptop. Everything works great, except the gnome desktop seems to be in denial. The desktop seems to be confined to the upper right 80% of the screen -- the top and bottom toolbars only go partway across the screen, and the bottom tool bar is not on the bottom of the screen, and the desktop icons are restricted to this area. New application windows launch into this area, but can be relocated or resized into the whole screen. The background, on the other hand, fills the whole screen.

It's kind of like Gnome hasn't gotten the message that the screen resolution went up.  Unfortunately, system->preferences->resolution gives me a drop down list that doesn't include the resolution that the screen is at.

Any ideas how I can get things back to normal?

---

### Post by mtopro on 2008-12-28
Not sure what graphics card you are using, but have also had a similar issue with only 'Twin View' enabled on the graphics card.  I believe you will need to setup the screens for 'Xinerama'.  If it is an Nvidia card, make sure the 3rd party drivers are enabled/installed. Then open as root and set to Xinerama.  Does that fix the issue?

---

### Post by dcottingham on 2008-12-28
Isn't xinerama for when you have multiple screens? I should have clarified, I'm not trying to use the external monitor and the laptop screen as two separate screens -- laptop and external are showing the same thing. (Or should I be using xinerama anyhow?)

My graphics card is ATI Radeon R250.

---

### Post by dcottingham on 2008-12-28
I've arrived at a guess about what Gnome is doing -- it sees that the laptop screen is 1024x768, so it's trying to make the desktop usable on the screen, which makes it look funny on the 1280x1024 external monitor.  (So I could probably solve the problem by convincing the external monitor to work at 1024x768, which I'm pursuing.)

But what I'd like is to force Gnome to use the 1280x1024 resolution, even though that puts it off the screen on the main display. Any ideas how this can be done?

---

