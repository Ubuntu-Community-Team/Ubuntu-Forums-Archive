---
title: "How to make terminal to open at the screen center?"
date: 2009-05-15
forum: General Help
---

### Post by zurih on 2009-05-15
Hey,

Is it possible to make the terminal to be always opened at the center of the screen?

Thanks in advance

---

### Post by kpkeerthi on 2009-05-15
If you are using compiz (desktop effects), you can try with this [tip]("http://phorolinux.com/quick-tip-configuring-fixed-window-placement-in-compiz-fusion.html").

---

### Post by zurih on 2009-05-15
> **kpkeerthi said:**
> If you are using compiz (desktop effects), you can try with this [tip]("http://phorolinux.com/quick-tip-configuring-fixed-window-placement-in-compiz-fusion.html").

No, I don't use Compiz. I disabled all of the special effects.

---

### Post by kpkeerthi on 2009-05-15
Try with devilspie.

[http://ubuntu-tutorials.com/2007/07/25/how-to-set-default-workspace-size-and-window-effects-in-gnome/]("http://ubuntu-tutorials.com/2007/07/25/how-to-set-default-workspace-size-and-window-effects-in-gnome/")

[https://help.ubuntu.com/community/Devilspie]("https://help.ubuntu.com/community/Devilspie")

**Hint: **You need to use the geometry action, like so:

(geometry WIDTHxHEIGHT+XPOSITION+YPOSITION)
[INDENT]- Set size and position.[/INDENT]
[INDENT]**Example: **(geometry 100x100+0+0) will make it 100 by 100 pixels large and put it into the top right corner[/INDENT]

---

### Post by zurih on 2009-05-15
My screen res is 1680x1050. So I wrote this:

```

(and (is (application_name) "gnome-terminal")
     (is (window_role) "")
        (begin
                (undecorate)
                (geometry "800x500+840+525")
        )
)

```

But I don't get how I actually use it

---

### Post by happyhamster on 2009-05-15
- Just call gnome-terminal like this:

gnome-terminal --geometry=60x30+500+200

- Note that 60x30 is the number of chars and lines, not the number of pixels, while the offset +500+200 is expressed in pixels. (Values are just an example.)
So, if you're using an icon to launch gnome-terminal, right-click that icon and choose Properties and make the desired change. If you're using the main menu: right-click it, choose Edit Menus and then Applications-->Accessories-->Terminal-->Properties-->etc.


Good luck, and keep us informed.

---

