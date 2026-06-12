---
title: "scrollbar too skinny"
date: 2009-06-22
forum: General Help
---

### Post by utnu on 2009-06-22
vertical scrollbar is less than 3/16" width

any way to increase the width ?

any userChrome.css code ?





[COLOR="LightBlue"].[/COLOR]

---

### Post by s.fox on 2009-06-22
Hi,

You can't set it with a GUI but it's easy to tweak the GTK theme.
First run this command
 ```

gedit ~/.gtkrc-2.0

```Now paste this in and then save it.
 ```
  
style "scroll"
{
GtkScrollbar::slider-width = 25
}
class "*" style "scroll" 
```Make sure you change the 25 to whatever width you like. 25 is pretty wide, I'm just using it as an example.
You can use the .gtkrc-2.0 file to control a lot of GTK widgets. Or you can edit the theme directly. I usually make a copy of the system theme and put it in ~/.themes before I edit those.

Information copied from [here]("http://ubuntuforums.org/showthread.php?t=255065").

-s.fox

---

### Post by utnu on 2009-06-22
[COLOR="Silver"].[/COLOR]
I'll leave it at 25 for now; it's just right.

problem Solved \\:D/ thank you

[COLOR="Silver"].[/COLOR]

---

