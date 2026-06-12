---
title: "gnome stuff in openbox?"
date: 2005-06-17
forum: Desktop Environments
---

### Post by kerinin on 2005-06-17
i've been playing around with my window manager, partly because i'm bored and partly because my laptop is slow.  i installed openbox and i like it a lot.  i realized that i can run

```
nautilus -n &
``` 

and the gnome desktop will pop up with the background i set for it and the contents of my ~/Desktop folder.  this made me wonder what else i could run from gnome without incurring the overhead of the full DE, so i tried 

```
gnome-panel &
``` 

that worked well but i get a lot of broken icons, and many of my applications have no icon at all.  what do i need to do to get the icons to display correctly - does gnome have it's own icon manager that's seperate from nautilus, and if so can i run it by itself?

also, am i crazy for doing all this?  i haven't used this set up enough to be able to tell what i'm missing out on - what does gnome DO really?

---

### Post by Moobert on 2005-06-17
> 
and the gnome desktop will pop up with the background i set for it and the contents of my ~/Desktop folder.

try:
```
nautilus --no-desktop &
```
> 
does gnome have it's own icon manager that's seperate from nautilus, and if so can i run it by itself?

run 
```
gnome-settings-daemon &
```
then config with:
```
gnome-theme-manager
```
> also, am i crazy for doing all this? i haven't used this set up enough to be able to tell what i'm missing out on - what does gnome DO really?

I do similar things with fluxbox, but I set my gtk themes using... gtk-theme-switch. As gnome-settings-daemon is abit of a ram hog. Gnome gives you preloading of thing like gtk and nautilus and an easy config system for gtk apps to link into.

---

