---
title: "Panels aren't themeable"
date: 2008-01-30
forum: Desktop Environments
---

### Post by drewcoon on 2008-01-30
I was downloading a few themes from gnome-look.org to try out, and now my panel no longer change color with the system theme (They are an ugly dark gray color).

Basically, I have an image skin over my bottom gnome panel, but the colors of the separators and the desktop switcher are grabbed from the system theme color of the panel. Now that the panel is no longer themeable, the switcher and separators are stuck as being dark gray.

I've removed all of the themes that I downloaded, rebooted several times, tried different theme colors  and controls, tried reinstalling gnome-panel, completely wiped my .themes and .icons folders, and my bars are still stuck as black :confused:

Does anyone have any ideas? I'm wondering if it's a control scheme that I downloaded that is causing the problem, but I can't figure out where the control schemes are stored.

---

### Post by rax_m on 2008-01-30
This maybe an obvious question, but have you checked the properties of the panel. Under the background tab you have the option to use the system theme or a custom background. 

You can get to the panel properties by right-clicking an empty space on your panel.

---

### Post by drewcoon on 2008-01-30
> **rax_m said:**
> This maybe an obvious question, but have you checked the properties of the panel. Under the background tab you have the option to use the system theme or a custom background. 

You can get to the panel properties by right-clicking an empty space on your panel.

Yes, I have two panels, the bottom one is set to use an image as a skin (if it's set to "use system theme" it comes out dark gray while the theme is actually a light grey color. The top bar is set to a solid color (black with a lot of transparency).

I believe that the workspace switcher and separators draw their color from the system theme, which isn't what I want because black separators and a black switcher aren't very appealing to me.

here's a pic that shows what I mean (It's a bit old, I fixed the white text on top panel issue).
[http://i16.photobucket.com/albums/b23/Drewc2k5/problem.png](http://i16.photobucket.com/albums/b23/Drewc2k5/problem.png)

---

### Post by rax_m on 2008-01-30
ah.. i see what you mean. Sorry, not sure if that can be fixed. Maybe someone else can help.

---

### Post by drewcoon on 2008-01-30
Oh I'm sure there is a way to fix it somewhere... Just gotta figure out how.

*bump*

BTW I tried editing color info in some XML files in my .gconf folder, I rebooted and they reverted to the way they were before I changed them. Scratch that idea.

---

