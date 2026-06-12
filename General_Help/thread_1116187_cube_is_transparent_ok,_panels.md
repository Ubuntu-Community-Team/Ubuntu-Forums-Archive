---
title: "cube is transparent ok, panels?"
date: 2009-04-04
forum: General Help
---

### Post by chriskin on 2009-04-04
while rotating, the cube is transparent , but the panels are not

i have not seen any option to make them transparent as well , is there any?

(i already have them fully transparent when the cube is not rotating, what i need is transparency when the cube rotates, so i can see through them)

:popcorn:

---

### Post by chriskin on 2009-04-04
i checked again and it is not just transparency, the panel doesn't get any compiz effect on it
why is that?

---

### Post by CatKiller on 2009-04-05
When the panel is transparent, it isn't actually transparent. It's just got an image background of that part of the wallpaper that's covered by the panel, so that you can still have a transparent panel on systems that can't do compositing.

I have no idea if the gnome-panel is going to get real compositing support in the future. I also haven't looked to see if there's a workaround, since I use AWN instead. There is a way to have the panel separate from the Desktop, so you can rotate the cube and have the panel not move. I don't know if that's something that you'd prefer.

---

### Post by chriskin on 2009-04-05
> **CatKiller said:**
> When the panel is transparent, it isn't actually transparent. It's just got an image background of that part of the wallpaper that's covered by the panel, so that you can still have a transparent panel on systems that can't do compositing.

I have no idea if the gnome-panel is going to get real compositing support in the future. I also haven't looked to see if there's a workaround, since I use AWN instead. There is a way to have the panel separate from the Desktop, so you can rotate the cube and have the panel not move. I don't know if that's something that you'd prefer.


thank you for the answer
i searched the compiz site and the where saying somewhere that they might hack the panel in the future , so i will just wait. when not rotating the cube, panels look like the are actually transparent, so there is no big problem

---

### Post by iiiears on 2009-04-05
Google this article on "Regex Matching" for a more complete explanation.
"Ars Technica"
"How to: Configuring conditional window transparency in Compiz Ryan Paul  | Published: November 08, 2007"

It can be reduced to these instructions.

1.) Install "compizconfig-settings-manager"

2.) Under the "General Settings" tab select "Opacity".

3.) In the Opacity Windows text field, you have to add a "|" the pipe symbol between the types of window decorations you want to add transparency to. Try this. 

Tooltip | Menu | PopupMenu | DropdownMenu

or.

Dock | tooltip | menu | poupmenu | dropdownmenu 

For an application like gedit.

!title=^gedit$ & !type=dialog

The "^" is useful because it escapes all text prior to the text you want to match.


A more complete list is here.

[http://wiki.compiz-fusion.org/WindowMatching](http://wiki.compiz-fusion.org/WindowMatching)

~Best Wishes.

---

### Post by chriskin on 2009-04-05
> **iiiears said:**
> Google this article on "Regex Matching" for a more complete explanation.
"Ars Technica"
"How to: Configuring conditional window transparency in Compiz Ryan Paul  | Published: November 08, 2007"

It can be reduced to these instructions.

1.) Install "compizconfig-settings-manager"

2.) Under the "General Settings" tab select "Opacity".

3.) In the Opacity Windows text field, you have to add a "|" the pipe symbol between the types of window decorations you want to add transparency to. Try this. 

Tooltip | Menu | PopupMenu | DropdownMenu

or.

Dock | tooltip | menu | poupmenu | dropdownmenu 

For an application like gedit.

!title=^gedit$ & !type=dialog

The "^" is useful because it escapes all text prior to the text you want to match.


A more complete list is here.

[http://wiki.compiz-fusion.org/WindowMatching](http://wiki.compiz-fusion.org/WindowMatching)

~Best Wishes.

can't see anything panel-related, i already use window opacity though

---

### Post by CatKiller on 2009-04-05
> **chriskin said:**
> can't see anything panel-related, i already use window opacity though

What iiiears means is that you could use an effect on windows of, for example, Class=Gnome-panel to apply some effect to the panels. Setting a general opacity value would probably make the panel applets transparent, too, but there might be something that you want to play with.

---

### Post by chriskin on 2009-04-05
> **CatKiller said:**
> What iiiears means is that you could use an effect on windows of, for example, Class=Gnome-panel to apply some effect to the panels. Setting a general opacity value would probably make the panel applets transparent, too, but there might be something that you want to play with.

not a bad idea at all :O

i will try it now :)

---

