---
title: "I want my top panel to be transparent, but it turns grey everytime"
date: 2009-07-19
forum: Desktop Environments
---

### Post by the8thstar on 2009-07-19
Hi all,

I am frustrated with Gnome. I have the Plastique Gtk theme installed and it won't let me replace the background panel with a semi-transparent background of my choice.

I am fiddling with /Home/.themes/Plastique/gtk-2.0/Panel/

In that folder there is a file called panel-bg.png which is the system default. Whenever I replace this file with another semi transparent image (with the same title), I obtain an ugly grey bar as my panel background picture.

What am I doing wrong here? Thanks for your help!

---

### Post by the8thstar on 2009-07-20
Bump

---

### Post by the8thstar on 2009-07-23
Bump

---

### Post by wojox on 2009-07-23
Why can't you right click the panel

Select Properties

Click Background Tab

Use Solid color 

Set Style to Transparent

---

### Post by mcduck on 2009-07-23
Is your new image the same size (as in dimensions, not filesize) as the original one? That might be necessary for the theme to apply the image correctly.

Also, have you tried setting the background image directly in the panel's preferences instead of doing it through the GTK theme? This way the size doesn't matter as you can enable scaling and/or rotation through gconf-editor, but you might have to remove all panel themeing from your GTK theme to get all panel applets to use the correct background image.

---

### Post by the8thstar on 2009-07-27
> **wojox said:**
> Why can't you right click the panel

Select Properties

Click Background Tab

Use Solid color 

Set Style to Transparent

> **mcduck said:**
> Is your new image the same size (as in dimensions, not filesize) as the original one? That might be necessary for the theme to apply the image correctly.

Also, have you tried setting the background image directly in the panel's preferences instead of doing it through the GTK theme? This way the size doesn't matter as you can enable scaling and/or rotation through gconf-editor, but you might have to remove all panel themeing from your GTK theme to get all panel applets to use the correct background image.

Thanks guys, I tried but I cannot make the bar fully transparent (only a few items have a transparent background).

---

### Post by eamon63 on 2009-07-27
CompizConfig Settings Manager > Opacity, Brightness, Saturation (under Accessibility) > Opacity Tab > NEW button > 

write/create an item called 

dock

then set opacity (e.g 85)....will also effect text however.

If you want full transparent with visible text, try to comment out the line "include panel.rc in gtkrc file, then go to panel properties and use solid color with opacity set to 0%.

---

### Post by the8thstar on 2009-07-28
> **eamon63 said:**
> CompizConfig Settings Manager > Opacity, Brightness, Saturation (under Accessibility) > Opacity Tab > NEW button > 

write/create an item called 

dock

then set opacity (e.g 85)....will also effect text however.

If you want full transparent with visible text, try to comment out the line "include panel.rc in gtkrc file, then go to panel properties and use solid color with opacity set to 0%.

That worked very well. Thank you for your help, **eamon63**.

---

