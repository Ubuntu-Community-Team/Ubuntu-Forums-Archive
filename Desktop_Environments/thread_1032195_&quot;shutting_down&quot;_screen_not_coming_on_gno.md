---
title: "&quot;shutting down&quot; screen not coming on gnome-screensaver"
date: 2009-01-06
forum: Desktop Environments
---

### Post by umang.ece on 2009-01-06
Hi folks  ,

 I m trying to implement "shutting down" screen for my system -ubuntu. 
while gnome-screensaver is active , on blank screen , I've to show my this shutdown screen. 

I used , 

display = gdk_display_get_default ();
screen = gdk_display_get_default_screen (display);
gtk_window_set_screen(GTK_WINDOW(window),screen);

attached the message to window , and show using "gtk_widget_show_all()". 

But This message screen is not coming onto my screensaver, but coming onto my Xfce-desktop,
Can anyone suggest y so happening ? How to get the display currently being used by gnome-screensaver and show my widget/image onto it ? ?

---

