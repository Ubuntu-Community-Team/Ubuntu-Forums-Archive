---
title: "[SOLVED] BlueSpace II window border theme doesn't work"
date: 2009-01-08
forum: General Help
---

### Post by INH on 2009-01-08
I installed the BlueSpace II theme, and the window border that came with it doesn't seem to work.  At first, the theme kept nagging me because it said the required engine 'ubuntulooks' was not installed.  So I installed that, but the BlueSpace II window border theme still shows up in the window border tab in System>Appearance>Customize window as 'default' and a big question mark on a white background.  

I got the BlueSpace II theme [here.](http://www.gnome-look.org/content/show.php/BlueSpace+II?content=78633)

---

### Post by Ivo Moelans on 2009-01-08
Could it be you are confusing some things? The window **borders** are not managed by gtk but by *emerald*.
In the comments the author writes that he uses this emerald theme in his screenshots: [http://gnome-look.org/content/show.php/radial?content=71352]("http://gnome-look.org/content/show.php/radial?content=71352").
You can install emerald themes with *System&#8594;Preferences&#8594;Emerald Theme Manager*.

Does this help?

Edit:
The reason you get a question mark is that this gtk theme doesn't include a *metacity* theme (which is what is used for the borders if you **don't** use compiz+emerald).
If you want to get rid of that, type in terminal:

```
gksudo gedit ~/.themes/BlueSpace_II/index.theme
```

Your text editor will open the theme index file. Change line 11, after *MetacityTheme=* from *default* in e.g. *Human* or any other metacity theme that is installed on your system. Those that you install are in */home/<username>/.themes*. System wide themes (for all users) are in */usr/share/themes*.
You could, if you wish, also change the icon theme that is to be used with this theme.

If anything of this is not clear (after you tried it), please ask again.

---

### Post by INH on 2009-01-08
Ah.  Yes, thank you, that was it. :) Thanks!

---

### Post by Ivo Moelans on 2009-01-08
You're welcome.
Please mark this thread as solved.

---

### Post by SPARTAN-118 on 2009-08-08
I know it's marked as [SOLVED], but I'd like to know:

Is there a way to get the Window Border?

*Without* Emerald?

Thanks, 
SPARTAN-118

---

