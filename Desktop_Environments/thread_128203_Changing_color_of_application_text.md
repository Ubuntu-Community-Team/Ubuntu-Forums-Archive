---
title: "Changing color of application text?"
date: 2006-02-10
forum: Desktop Environments
---

### Post by siorai on 2006-02-10
I've been playing around with altering my Gnome theme, but I have on problem. The text in most application windows is far too light and I'm not sure what needs to be changed to fix it. 

[IMG]http://siorai.com/stuff/menu.jpg[/IMG]

As you can see in the section I circled, the text is almost invisible. Now I know that I need to alter the value in the gtkrc file, but I'm not too sure which one I need to change.

---

### Post by cdhotfire on 2006-02-10
text[NORMAL]	       Normal Text
  text[PRELIGHT]       ????????????(have no idea)
  text[ACTIVE]	       Text Active (Right click of a file in nautilus)
  text[SELECTED]      Text Selected
  text[INSENSITIVE]   Text in the background (non active window)

Is this enough?

---

### Post by siorai on 2006-02-10
Unfortunately, when I change the text normal color, it would be visible in that section, but not on the rest of the window.. :???: So I got around in by changing the bg normal color to something darker. Not a perfect solution, but it's definitely a step in the right direction. Thanks.

---

### Post by cdhotfire on 2006-02-10
I see what you mean, your background is black, so if you change your text color to black that becoms invisible, but if you change it to white the other part becomes invisible.  Only way is to lower the darkness of your black background, good choice. :)

Anyways, no problem.

Good luck.

---

