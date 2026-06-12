---
title: "Top panel text color"
date: 2006-06-06
forum: Desktop Environments
---

### Post by BenevolentParty on 2006-06-06
hello all, i rarely post because all i need has already been posted, which is one of the great aspects of ubuntu :D!! i have just one question, does anyone know how to change the color of the text in the top panel of gnome? (i.e. Applcations, Places, System) i have a black wallpaper and would like to make the panel transparent. No one could read it if its black text, i would like to change it to white or gray...

thanks once again,

Chris

---

### Post by riddlermarc on 2006-10-24
Bumping this, it's exactly the question I'm looking to answer too :)

---

### Post by metalheart on 2006-10-24
Answered somewhere else.

[http://brentroos.com/2006/07/07/change-gnome-panel-text-color/](http://brentroos.com/2006/07/07/change-gnome-panel-text-color/)

---

### Post by riddlermarc on 2006-10-24
> **metalheart said:**
> Answered somewhere else.

[url]http://brentroos.com/2006/07/07/change-gnome-panel-text-color/[/ur]
I tried this but to no avail.. I didn't appear to have a .gtkrc-2.0 file so I created it in my /home/marc directory and chmodded it to 777.. then I uncommented the "# fg[NORMAL] = “#ffffff”" line and did a "killall gnome-panel" to restart the gnome panel but it hasn't changed, the text is still black ](*,)

[IMG]http://img436.imageshack.us/img436/4059/screenshotiv9.jpg[/IMG]

---

### Post by Lord Illidan on 2006-10-24
That didn't work for me either.. What I did was add these lines to
the .gtkrc-2.0 file.

```
style "my_color"
{
font_name = "DejaVu Sans 9"
fg[NORMAL] = "#ffffff"
}

widget "*PanelWidget*" style "my_color"
#widget "*PanelApplet*" style "my_color"
widget_class "*.Panel*GtkLabel" style "my_color"
```you can change font_name to any font you prefer.
And fg[NORMAL] to any colour you prefer..just use hex numbers.. FFFFFF is white..

EDIT : you should have a pristine .gtkrc-2.0 file in your home directory

---

### Post by riddlermarc on 2006-10-25
> **Lord Illidan said:**
> That didn't work for me either.. What I did was add these lines to
the .gtkrc-2.0 file.

```
style "my_color"
{
font_name = "DejaVu Sans 9"
fg[NORMAL] = "#ffffff"
}

widget "*PanelWidget*" style "my_color"
#widget "*PanelApplet*" style "my_color"
widget_class "*.Panel*GtkLabel" style "my_color"
```you can change font_name to any font you prefer.
And fg[NORMAL] to any colour you prefer..just use hex numbers.. FFFFFF is white..

EDIT : you should have a pristine .gtkrc-2.0 file in your home directoryExcellent, worked like a charm - thanks very much :)

---

### Post by gwayne on 2006-12-16
> **Lord Illidan said:**
> That didn't work for me either.. What I did was add these lines to
the .gtkrc-2.0 file.

```
style "my_color"
{
font_name = "DejaVu Sans 9"
fg[NORMAL] = "#ffffff"
}

widget "*PanelWidget*" style "my_color"
#widget "*PanelApplet*" style "my_color"
widget_class "*.Panel*GtkLabel" style "my_color"
```you can change font_name to any font you prefer.
And fg[NORMAL] to any colour you prefer..just use hex numbers.. FFFFFF is white..

EDIT : you should have a pristine .gtkrc-2.0 file in your home directory

Woot, your code fixed this for me, none of the others seemed to work for me on 6.10.

p.s. did you play on illidan in wow?

Ack

---

### Post by croppyboy on 2006-12-18
> **Lord Illidan said:**
> That didn't work for me either.. What I did was add these lines to
the .gtkrc-2.0 file.

```
style "my_color"
{
font_name = "DejaVu Sans 9"
fg[NORMAL] = "#ffffff"
}

widget "*PanelWidget*" style "my_color"
#widget "*PanelApplet*" style "my_color"
widget_class "*.Panel*GtkLabel" style "my_color"
```you can change font_name to any font you prefer.
And fg[NORMAL] to any colour you prefer..just use hex numbers.. FFFFFF is white..

EDIT : you should have a pristine .gtkrc-2.0 file in your home directory

Thanks! I've been trying to figure this out . . . worked like a charm on Edgy!

---

### Post by Lord Illidan on 2006-12-19
> **gwayne said:**
> Woot, your code fixed this for me, none of the others seemed to work for me on 6.10.

p.s. did you play on illidan in wow?

Ack

Not exactly my code (google is your friend, and no, I don't have WoW, but I did play Warcraft 3...loved Illidan).

---

### Post by Warprunner on 2008-03-20
> **Lord Illidan said:**
> That didn't work for me either.. What I did was add these lines to
the .gtkrc-2.0 file.

```
style "my_color"
{
font_name = "DejaVu Sans 9"
fg[NORMAL] = "#ffffff"
}

widget "*PanelWidget*" style "my_color"
#widget "*PanelApplet*" style "my_color"
widget_class "*.Panel*GtkLabel" style "my_color"
```you can change font_name to any font you prefer.
And fg[NORMAL] to any colour you prefer..just use hex numbers.. FFFFFF is white..

EDIT : you should have a pristine .gtkrc-2.0 file in your home directory

Thank you...fast and easy and worked perfect!!!

---

