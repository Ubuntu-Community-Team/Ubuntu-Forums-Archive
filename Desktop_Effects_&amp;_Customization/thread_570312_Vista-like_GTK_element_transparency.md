---
title: "Vista-like GTK element transparency?"
date: 2007-10-08
forum: Desktop Effects &amp; Customization
---

### Post by cameronw on 2007-10-08
Does anyone know how to (or if it's possible) to make GTK elements transparent (not pseudo transparency) such as Terminal using Compiz. I'm trying make the background of application semi-transparent and use the Alpha Blur=Normal to create a Vista like effect such as in their Gadget Manager. Terminal does this well but I just wondered if it can be used elsewhere.

[IMG]http://www.windowsvistauserguide.com/vista2/sidebar_gadgets/drag_the_desired_gadget_onto_the_sidebar.JPG[/IMG]

---

### Post by loell on 2007-10-08
i think its possible, but programmatically , so each app must change it.

i think it should use Cairo with set translucence.

---

### Post by cameronw on 2007-10-08
Im not quite sure but it's Cairo that renders the widgets isn't it? Maybe you can set psuedo-transparency with Cairo and Compiz senses that and changes it to use real transparency. That's what seems to happen with Terminal

---

### Post by Quikee on 2007-10-09
> **cameronw said:**
> Im not quite sure but it's Cairo that renders the widgets isn't it? Maybe you can set psuedo-transparency with Cairo and Compiz senses that and changes it to use real transparency. That's what seems to happen with Terminal

No... terminal asks through GTK if you are running in a composite environment and sets the type of transparency accordingly. You can not set this without code change but it should not be too difficult to adapt.

---

