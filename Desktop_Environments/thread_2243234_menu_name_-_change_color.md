---
title: "menu name? - change color"
date: 2014-09-07
forum: Desktop Environments
---

### Post by Claus7 on 2014-09-07
Hello,

does anyone have any idea how the menu that appears while placing my mouse cursor on the terminal icon is called, so as to change its color from black to sth else?

I think that I have to choose the gnome color chooser for that.

Thank you in advance,
Regards!

---

### Post by Claus7 on 2014-09-07
Hello,

(ubuntu trusty 64bit-compiz flashback)
I was using Radiance theme so I went to /usr/share/themes/Radiance/gtk-3.0/

and there I found the file: gtk-main.css

and I changed the (under /*default color scheme */):
@define-color tooltip_bg_color #000000;
@define-color tooltip_fg_color #ffffff;

to
@define-color tooltip_bg_color #ffffff;
@define-color tooltip_fg_color #000000;

In order to see what the colors mean go to:
[http://www.color-hex.com/color/f07746](http://www.color-hex.com/color/f07746)

Log out and back in, in order to see the changes taking effect.

Regards!

PS: the menu that appears is the hover popup menu, while placing the mouse on top of icons

---

### Post by vasa1 on 2014-09-07
> **Claus7 said:**
> Hello,

(ubuntu trusty 64bit-compiz flashback)
...

Maybe you can update your profile to indicate you're no longer using Ubuntu 10.10.

---

### Post by CantankRus on 2014-09-07
You should be able to make the change for all themes by
adding those values to **~/.config/gtk-3.0/gtk.css**
eg 
```
gedit ~/.config/gtk-3.0/gtk.css
```
and paste in your code...
```
@define-color tooltip_bg_color #ffffff;
@define-color tooltip_fg_color #000000;
```

---

### Post by vasa1 on 2014-09-07
> **CantankRus said:**
> You should be able to make the change for all themes by
adding those values to **~/.config/gtk-3.0/gtk.css**
eg 
```
gedit ~/.config/gtk-3.0/gtk.css
```
and paste in your code...
```
@define-color tooltip_bg_color #ffffff;
@define-color tooltip_fg_color #000000;
```
I've been using a slightly different approach. I put stuff into ~/.config/gtk-3.0/**settings.ini**.

---

### Post by CantankRus on 2014-09-07
> **vasa1 said:**
> I've been using a slightly different approach. I put stuff into ~/.config/gtk-3.0/**settings.ini**.
Oh ok, so that works too. :KS

I just used **~/.config/gtk-3.0/gtk.css** because this is the file that gtk-theme-config creates.

---

### Post by vasa1 on 2014-09-08
> **CantankRus said:**
> Oh ok, so that works too. :KS

I just used **~/.config/gtk-3.0/gtk.css** because this is the file that gtk-theme-config creates.
That's the one that Xubuntu has included recently. The dev blogged about here: [http://worldofgnome.org/customizing-gtk-themes-just-got-easier/](http://worldofgnome.org/customizing-gtk-themes-just-got-easier/)
I used it for a short time.

---

### Post by Claus7 on 2014-09-08
Hello,

thank you about your answers. I did not use a .xxx folder (with a dot in front), because I was not able to do the same thing with some icons. I think that your solution is more error free, which means that if something goes wrong it won't affect as much.

My signature would change in the near future, it is just that I was really happy with maverick 10. I hope that with the info I provide in my posts/threads people understand about the D.E. that I'm using.

Thank you for your answers,
Regards!

---

### Post by vasa1 on 2014-09-08
> **Claus7 said:**
> ...
My signature would change in the near future, it is just that I was really happy with maverick 10. I hope that with the info I provide in my posts/threads people understand about the D.E. that I'm using.
...
Things related to GNOME seem to be evolving pretty fast. I see no reason not to provide the correct information in a timely manner. I didn't see anything in the first post to help me understand the version involved. The DE may remain the same and yet be very different. So GNOME 2 !== GNOME 3. Anyway, you have the freedom to do what you want. Just so you know that someone could be misled.

---

