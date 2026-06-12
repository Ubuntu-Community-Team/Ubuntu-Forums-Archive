---
title: "Redmond skin modification?"
date: 2012-06-12
forum: Desktop Environments
---

### Post by ineuw on 2012-06-12
I am a dual boot WinXP/Xubuntu newbie who works with text and prefers the simple life. I selected Redmond skin as the easiest to get used to during the transition phase to Linux. My only problem is how to make minor changed in the colors. For example, I want to change the dark blue row highlight to another color, etc. Is this possible and how?

I am using Xubuntu 12.04.

---

### Post by Toz on 2012-06-13
You have a number of choices.

If you want to make the change system-wide to the actual theme file itself, then edit the file: /usr/share/themes/Redmond/gtk-2.0/gtkrc and replace the line:
>   base[SELECTED]    = { 0.04, 0.14, 0.41 }
...with
```

  base[SELECTED]    = "#FF0000"
```
...and replace #FF0000 with the colour code that you want. The application gcolor2 can help you find these color codes (they are hexidecimal representations of RGB values).

.

If you want to make the change to a specific user and that user will only use this theme file, then create the file ~/.gtkrc-2.0 (in each user's home directory) with the following content:
```
style "my-redmond-hacks"
{
  base[SELECTED]    = "#FFFF00"
}
class "GtkWidget" style "my-redmond-hacks"

```
...this will force the "row highlight" colour to be the same for ALL themes.

.

And finally, if everyone on the system will only use the redmond theme and you want to make the change once so that it affects everyone, add the above snippet to /etc/gtk-2.0/gtkrc.

---

### Post by ineuw on 2012-06-13
Toz, Many thanks! It's simplicity in itself. Also, I am a single user and no one comes near this desktop.

---

