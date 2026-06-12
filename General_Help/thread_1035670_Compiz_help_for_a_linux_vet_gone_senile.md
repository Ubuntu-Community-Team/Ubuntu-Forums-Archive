---
title: "Compiz help for a linux vet gone senile?"
date: 2009-01-10
forum: General Help
---

### Post by kdarkentity on 2009-01-10
It's been over a year since i have used linux religiously and i have since forgotten a few things regarding compiz. 

First question is where in the compiz config settings menu do i edit the transparency of the popupmenu? (gnome menu)

Second question is what is the keyboard command to use the scroll bar to make windows and panels or whatever the mouse is hovered over more or less transparent?

Thank you.

---

### Post by blackened on 2009-01-10
> **kdarkentity said:**
> ...First question is where in the compiz config settings menu do i edit the transparency of the popupmenu? (gnome menu)...

Opacity, Brightness and Saturation -> Under "Window Specific Settings" click "New". In the subsequent dialog enter the following into the box labeled "Windows", then adjust the transparency settings to your liking:

```
name=gnome-panel & type=dropdownmenu
```

---

