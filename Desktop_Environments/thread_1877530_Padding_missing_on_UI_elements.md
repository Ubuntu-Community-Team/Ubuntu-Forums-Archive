---
title: "Padding missing on UI elements"
date: 2011-11-08
forum: Desktop Environments
---

### Post by mikrogroove on 2011-11-08
As can be seen from the attached screengrab, the UI looks very squished up in my standard Xubuntu installation with XFCE 4.8 - as if the text elements have almost no padding at all. All application dialogs and menus display as a horrible mess of text that is really frustrating to use. I've tried changing fonts and "themes" but they all have the same problem. How can I get better separation of the UI elements? Any suggestions much appreciated!

---

### Post by mikrogroove on 2011-11-09
Ok so if that screengrab failed to convince anyone that there is a problem, this unreadable mess is what I saw when on my way to the #xubuntu IRC (where I was met with equal disinterest).

---

### Post by Toz on 2011-11-09
I don't know, the screenshots look pretty much okay to me. Here is a screenshot of my Thunderbird preferences screen. You seem to have a different theme. Have you tried changing the the theme from both the "Appearance" and "Window Manager" modules in Settings Manager?

---

### Post by mikrogroove on 2011-11-09
> **Toz said:**
> I don't know, the screenshots look pretty much okay to me. Here is a screenshot of my Thunderbird preferences screen. You seem to have a different theme. Have you tried changing the the theme from both the "Appearance" and "Window Manager" modules in Settings Manager?

Thanks for the reply Moz. The only thing that changes anything is changing the font (obviously) but only because different fonts have different letter-height. Do you know if there is any way to increase  the line-height/padding/margins/spacing/whatever? I'm getting a headache  from this cluttered UI :(

---

### Post by Toz on 2011-11-09
Have a look at the gtkrc file for your particular theme. It is usually found at /usr/share/themes/<theme_name>/gtk-2.0/gtkrc (for gtk2 themes) and/or settings.ini at /usr/share/themes/<theme_name>/gtk-3.0/ (for gtk3) themes. You can make the changes directly to those files (will affect all users) or add the changes to ~/.gtkrc-2.0 or ~/.config/gtk-3.0/settings.ini (for user-specific configurations).

For further information about what the settings are and what they do, look at these references:
- gtk2 - [http://developer.gnome.org/gtk/2.24/]("http://developer.gnome.org/gtk/2.24/")
- gtk3 - [http://developer.gnome.org/gtk3/stable/]("http://developer.gnome.org/gtk3/stable/").

Admittedly, its a bit of a heady topic. Google might help.

---

### Post by mikrogroove on 2011-11-10
Ahhh... that's great,many thanks! I was very quickly able to increase the spacing of elements in dialog boxes and the padding on buttons too - will have a look at those links for more!

---

