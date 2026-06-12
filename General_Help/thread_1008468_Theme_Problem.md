---
title: "Theme Problem"
date: 2008-12-11
forum: General Help
---

### Post by IceReaver75 on 2008-12-11
I have tried installing this theme from gnome-look:

[http://gnome-look.org/content/show.php/BlueSpace+II?content=78633](http://gnome-look.org/content/show.php/BlueSpace+II?content=78633)

when installed the theme manager is saying this theme wont look like intended because window manager "default" isn't installed.

Anyone know what that means?

---

### Post by gettinoriginal on 2008-12-11
metacity is the default window manager, check synaptic to make sure it is installed, and if it is, then check reinstall and go from there. :p

---

### Post by Ivo Moelans on 2008-12-11
In the directory */home/<username/.themes/Bluespace_II/* is a file also called *Bluespace_II*, the index.theme file. This can be opened with Text Editor with superuser privileges (terminal: *sudo gedit*). This file tells the theme where to look for its components. On line 11 you'll find

```
MetacityTheme=default
```

Change *default* with the name of a Metacity theme you know is installed on your system, e.g. *Human*. You can also define which icon and cursor theme it should use.

That's it.

---

### Post by IceReaver75 on 2008-12-11
still having a problem with this theme.....now the theme manager is complaining about gtk+ theme "" is not installed.

I already went through the gtkrc file and filled in all the theme engines and checked the custompanel and panel files for any empty engines and didnt see any.

so with all engines filled in i dont understand why it is still complaining that the theme "" isnt installed

---

### Post by Shwefty on 2008-12-11
Well, this isn't an answer to your problem, but a suggestion to go in a different direction.  I use Emerald Theme Manager (same gnome-look site, but its themes are under Beryl).  And I've found you can get some nifty looking themes out of it.

So, if this problem goes unresolved, you can always give that a shot!

---

### Post by Ivo Moelans on 2008-12-12
Did you perhaps miss the one on line 125 in panel.rc?

---

### Post by IceReaver75 on 2008-12-12
Yes I did forget that one.  Thanks again.   After looking at all those lines in 3 different rc files everything begins to look the same and blend together after while.

---

### Post by Ivo Moelans on 2008-12-12
Glad everything is OK now. A tip: use the search function in Text Editor (*Search&#8594;Find* and *Find Next* or *Ctrl+F* and *Ctrl+G*) for looking up strings. Makes a boring job very fast.

---

### Post by IceReaver75 on 2008-12-12
Alright this may be a stupid question but which folder is it better to put the theme in ....your home .theme folder or into your usr/share/theme folder.  Also would it cause conflicts of you put a copy into both folders?

---

### Post by Ivo Moelans on 2008-12-12
I don't think it's a question of 'better'. The difference is that themes in the /usr/share/theme folder are system wide, i.e. are available for all users. In your home directory they are (obviously) only available for you. But if you put them there and make a backup of your home directory they are still available, with all changes you made in them, when you perform a clean install and copy the backup in the new home directory.
As for your second question: I have done it with one theme and it simply shows up twice in the Appearance Preferences, apparently without causing conflicts.
And by the way, there are no stupid questions. There could be stupid answers however.

---

