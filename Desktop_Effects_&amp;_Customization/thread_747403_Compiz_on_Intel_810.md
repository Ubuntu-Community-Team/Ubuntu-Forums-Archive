---
title: "Compiz on Intel 810"
date: 2008-04-06
forum: Desktop Effects &amp; Customization
---

### Post by collinp on 2008-04-06
Ok, when i try to enable Compiz on a Intel 810 Integrated Graphics, the screen flashes a few times, then returns to its state before the flashes. When i try to do any of the special effects, it does nothing. What i need to know is how do i get compiz to work on a intel 810 gfx set? Im running Ubuntu 7.10, gotta change what the bar says.

---

### Post by collinp on 2008-04-06
Dosent look like im gonna get much help here.

---

### Post by rbenchley on 2008-04-06
Try the setup instructions:

[http://www.compiz.org/Documentation/Documentation]("http://www.compiz.org/Documentation/Documentation")

---

### Post by Locutus_of_Borg on 2008-04-06
what driver do you have in xorg.conf?


also what output do you get when you start compiz from the terminal?

also also check that you have direct rendering enabled
```
glxinfo
```

if not, enable it in xorg.conf

there are a few other factors that may be preventing compiz, but i cannot remember, but thats a start at least

---

### Post by joelito on 2008-04-23
I have a similar problem, direct rendering works as confirmed by glxgears, glxinfo and quake 2. But when I try to enable desktop effects, it doesn't work. I really don' t wanna use my hammer on this one :D.

---

