---
title: "how to get gtk theme going in fluxbox"
date: 2008-04-30
forum: Desktop Environments
---

### Post by nephish on 2008-04-30
Hey there all, 
I am running on 8.04, and i like running gnome sometimes, but just seem to get stuff done more efficiently in fluxbox. I don't like the themeless fluxbox though, and i am wondering how to get my gnome and gtk themes to work in fluxbox for when i run gtk apps like nautilus?

thanks

---

### Post by RedSquirrel on 2008-05-06
You could install **gtk-chtheme** and use it to set your theme. It will create the file ~/.gtkrc-2.0.

OR

Manual method: create a ~/.gtkrc-2.0 file with your favourite text editor and add, for example:

```
gtk-theme-name = "Human"
```

For icons, I use:

```
gtk-icon-theme-name = "Tango"
```

---

### Post by nephish on 2008-05-06
Thanks RedSquirl, i appreciate it a lot. Worked great !

---

