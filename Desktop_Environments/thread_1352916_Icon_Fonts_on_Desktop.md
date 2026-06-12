---
title: "Icon Fonts on Desktop"
date: 2009-12-12
forum: Desktop Environments
---

### Post by Narusegawa on 2009-12-12
How can I get some smoother icon text on my desktop? I know I can do this in windows as it puts a shadow behind so I can read these icons but not sure how to get ubuntu/gnome to do that.

I have a mostly white background. All visual effects are turned on aswell. Metacity I think it's what's being used (this is pretty much a default 9.10 install).

As you can see the text on the icons is extremely hard to see in the attachment.

---

### Post by benerivo on 2009-12-12
I don't think you can get much more of a shadow effect than you already have. It's just that the light source is roughly top left so that only the bottom right of character edges appear in shadow. You could make you desktop icon text appear black by creating a new file with...```
gedit .gtkrc-2.0
```and putting in this code...```
style "desktop-icon"
{
NautilusIconContainer::frame_text = 1
text[NORMAL] = "#000000"
NautilusIconContainer::normal_alpha = 0
}
class "GtkWidget" style "desktop-icon"

```Then log off and back in.

---

### Post by roggenschrotbrot on 2009-12-12
you could also want try gnome-color-chooser to change your icon's font color or place a uni color rectangle behind the icon description (as seen in older windows versions). its fairly easy to use and quite powerful, a recommended install to any gnome user imho.

---

