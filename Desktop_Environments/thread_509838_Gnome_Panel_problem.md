---
title: "Gnome Panel problem"
date: 2007-07-25
forum: Desktop Environments
---

### Post by jefrazie on 2007-07-25
Hey Im trying to customize my panel with an image. I am able to apply this image as seen in the screenshot but you can see i still have a portion of the panel that is showing up black for some reason, this portion contains my volume, calendar and notification area. How do i go about making that portion of the panel the same as the rest? Thanks[http://s167.photobucket.com/albums/u123/jefrazie/?action=view&current=Screenshot.png]("http://s167.photobucket.com/albums/u123/jefrazie/?action=view&current=Screenshot.png")

---

### Post by rsambuca on 2007-07-25
This isn't exactly what you are asking, but you could change your desktop wallpaper by adding the taskbar image onto it using gimp.  You can then just make the panel transparent.

I have done this before.

---

### Post by mcduck on 2007-07-26
The problem is your GTK theme that sets it's own background for panels. You could open it's gtkrc file and try to finsd the line that defines panel background & remove it. Other than that the only way is to use some other GTK theme.

---

### Post by jefrazie on 2007-07-26
> **mcduck said:**
> The problem is your GTK theme that sets it's own background for panels. You could open it's gtkrc file and try to finsd the line that defines panel background & remove it. Other than that the only way is to use some other GTK theme.

yep that fixed it, played around with the gtk theme and finally got it working, thanks

---

