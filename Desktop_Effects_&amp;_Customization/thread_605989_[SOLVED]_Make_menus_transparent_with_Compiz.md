---
title: "[SOLVED] Make menus transparent with Compiz?"
date: 2007-11-07
forum: Desktop Effects &amp; Customization
---

### Post by sci-fi guy on 2007-11-07
enough said

---

### Post by jimerickso on 2007-11-07
go to compizconfig settings manager
go to general options
go to opacity settings tab
enter the following in the winow opacities table:
tooltip 85
dropdownmenu 85
popupmenu 85
dock 85

this will make your dock, menus, and tool tips transparent. you can enter any value you want but they get hard to read below 85 for me anyway. good luck!

---

### Post by sci-fi guy on 2007-11-07
Neat! Is there an option for specific windows? i.e. Gimp is fully opaque and the terminal is transparent?

---

### Post by jimerickso on 2007-11-07
to make terminal transparent open gnome-terminal (thats what i use) and:

go to edit
go to current profile
go to the effects tab
select transparent background
move slider to desired transparency (i use "none", this makes terminal completely transparent)

now that i think about it i may have misunderstood your last post. let me look through ccsm a bit and i will get back to you. disregard what i said above unless you want a transaprent terminal. more in a bit...

---

### Post by jimerickso on 2007-11-07
> **sci-fi guy said:**
> Neat! Is there an option for specific windows? i.e. Gimp is fully opaque and the terminal is transparent?
i know of no way to make individual application menus transparent. sorry!

---

### Post by sci-fi guy on 2007-11-07
Thanks anyways.

You had it (mostly) right the first time.  I was asking because when I would set transparency in the terminal settings, it would show only the desktop behind the terminal, and none of the windows. But that seems to be fixed now. I can clearly see Firefox through the terminal.

---

### Post by DjBones on 2007-11-07
if its any consolation though,
you can set windows to a desired transparency by holding down <alt> and scrolling up or down on the window..
nifty feature, but it doesn't save the settings to my knowledge

---

### Post by Number6 on 2007-11-07
> go to compizconfig settings manager

..and where is this exactly? It's not on any menu on my system!

---

### Post by SomeGuyDude on 2007-11-07
> **Number6 said:**
> ..and where is this exactly? It's not on any menu on my system!

System -> Preferences -> Advanced Desktop Effects Settings

I don't have a clue why putting it under "Compiz" didn't occur to these guys, but there ya go.

---

### Post by sci-fi guy on 2007-11-07
IIRC, you must install 'compizconfig-settings-manager' from the repos first.

---

### Post by jimerickso on 2007-11-07
sorry guys i compiled from git so mine shows up in preferences as compiz config settings manager. i will try to remember that for future reference its advanced desktop effects for users of the default set up. my bad!!

---

### Post by psyopper on 2007-11-07
For what it's worth, you CAN make specific applications apply to the transparency setting by using Window Matching Rules. Check out the [Window Matching Rules ]("http://wiki.compiz-fusion.org/WindowMatching")page on the [Compiz-Fusion Wiki]("http://wiki.compiz-fusion.org").

---

### Post by jimerickso on 2007-11-07
thanks psyopper i learned something new today! i will try it tonight.

---

