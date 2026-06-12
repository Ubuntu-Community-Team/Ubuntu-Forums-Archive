---
title: "Building themes, GTK2.0/Metacity?"
date: 2007-05-03
forum: Desktop Effects &amp; Customization
---

### Post by Taigrr on 2007-05-03
I'm interested in building, and more so modifying, themes. But I can't seem to track down any info reguarding what does what. For instance, what is the diffrence between GTK2.0 and Metacity? And what do I change to modify how things "light" when you click them. For instance,  minimized windows on the bottom of the screen, or IM window flashing, or when you click "Applications", "Places" or "System".

Thank you for any help!

---

### Post by ppan76 on 2007-05-04
If you want to theme the min,max or close button then you need to create a metalcity theme. Or create a theme for any of the many Windows Decorators outhere.  (ie Emerald).

GTK themes is mostly for the Gnome Panel, fonts, colors schemes, and color of the window bars.

---

### Post by Taigrr on 2007-05-04
Okay, so if I have a GTK theme enabled right now, would I then run Metacity over the top/along with it, or is it one or the other?

---

### Post by j.miller565 on 2007-05-04
so how do you change GTK 2.0 themes? Is there a program for it?

---

### Post by Pox on 2007-05-04
GTK2.0 manages the appearance of the contents of your window - everything excluding the borders and the titlebar.
Metacity handles the borders and the titlebar and is a Window Manager / Window Decorator in one.

To switch GTK themes, go to your theme settings - have a hunt, not sure where it is in GNOME.

To modify a GTK theme, you need to manually change the .gtkrc file with a text editor.  This file is found within the folders of a GTK theme, usually in /usr/share/themes/ or ~/.themes/.

---

