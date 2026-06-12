---
title: "Window Title Font"
date: 2009-06-05
forum: Desktop Environments
---

### Post by dullo on 2009-06-05
I don't know if this infromation will help but i'll post it now so i'm not asked for it later.
I'm running Jaunty 9.04
Gnome Desktop Environment

I was wondering if you can take the window title font and instead of it being on the left of the title bar. Is it possible to center the font in the middle of the title bar?

---

### Post by dullo on 2009-06-06
bump.

---

### Post by coffeecat on 2009-06-06
> **dullo said:**
> I was wondering if you can take the window title font and instead of it being on the left of the title bar. Is it possible to center the font in the middle of the title bar?

I'm mystified. In a default gnome desktop the window title is in the centre of the title bar. If you do really mean a window title bar perhaps you could post a screenshot to show what you mean.

If you mean the main menu at the left of the top panel, that's a different matter. The main menu is the one that has the Ubuntu logo to the left, and then 'Applications', 'Places' and 'System' drop-dowm menus. If you want to move that, right-click on it and untick 'lock to panel'. Now right-click again and click on 'Move'. If you now move the mouse pointer to the horizontal position you want, the menu will follow you. Simply left-click to stop moving it. You may wish to relock it again.

---

### Post by dullo on 2009-06-06
[IMG]http://i44.tinypic.com/15n99j7.png[/IMG]
i want to take the font circled in black and move it to the middle(where the red is)

---

### Post by Viva on 2009-06-06
If you're using emerald, you can customize the title bar(including the position of the title) in emerald theme manager

---

### Post by dullo on 2009-06-06
i'm not using emerald, is there any other way?

---

### Post by hictio on 2009-06-06
Is that happening to all the windows on your system?
What theme are you running, have you tried, just for testing, to use another theme and see if the the problem continues?

---

### Post by Xgen on 2009-06-06
I usually change that information under emerald (easier) but I believe that the title bar information is in your theme folder (usr/share/themes/name of theme)...under metacity-1/metacity-theme-1.xml.

---

### Post by dullo on 2009-06-06
i am using the Dust Sand theme right now, and you guys are right. if i switch the theme to Clearlooks it puts the font in the center. How can i get it to the center using the Dust Sand Theme?

---

### Post by hictio on 2009-06-06
> **dullo said:**
> i am using the Dust Sand theme right now, and you guys are right. if i switch the theme to Clearlooks it puts the font in the center. How can i get it to the center using the Dust Sand Theme?

Mmmhhh.... I'm not an expert in creating or editing themes, but, I´d begin by taking a look at the file 'gtkrc' on the directory:
```

/usr/share/themes/Dust Sand/gtk-2.0/

```

Issue a 'less' within a Terminal to page thru the file, it is a plain text file, and you won't be able to modify it unless you run a text editor via sudo on it.
To see the changes, you have to at least, change to another theme and then get back to that one.

---

### Post by Xgen on 2009-06-06
Another way, if preferable, is to go into the Appearance menu-->theme-->customize and change the window border theme for Dust Sand.

---

