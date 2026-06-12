---
title: "emerald window manager?"
date: 2007-10-13
forum: Desktop Effects &amp; Customization
---

### Post by kamitsukai on 2007-10-13
i recentley installed emerald window manager but when i try to change the theme (i presume you just select it?) it doesent change so i did somke research and i tried this:

```
emerald --replace
```

but it did squat:(

---

### Post by gsiliceo on 2007-10-13
> **kamitsukai said:**
> i recentley installed emerald window manager but when i try to change the theme (i presume you just select it?) it doesent change so i did somke research and i tried this:

```
emerald --replace
```

but it did squat:(

Please be more specific, what happened exactly?, the window borders are gone, do you have beryl or compiz or none?

To return to the usual windows manager

metacity --replace

---

### Post by kamitsukai on 2007-10-13
well thats just it! it didnt do anything :P and i have compiz and im trying to set a theme

---

### Post by Antiparadigm on 2007-10-13
I too am having a very similar problem as kamitsukai.

I can open emerald-theme-manager up just fine, but when I select a theme to use, it doesn't change (immediatly).  The next time I log in it will change.

I have tried to run:
```
emerald --replace
```

after I select the theme, but then I loose all window borders, and have to restart gnome.  Then I see the theme I selected.

I have tried to run it in a command line so I could get some sort of error, but I don't get much.
Here is the output of a emerald --replace:

```

<name>@<hostname>:~$ emerald --replace

(emerald:10703): Wnck-WARNING **: Unhandled action type (nil)

(emerald:10703): Wnck-WARNING **: Unhandled action type (nil)

(emerald:10703): Wnck-WARNING **: Unhandled action type (nil)

(emerald:10703): Wnck-WARNING **: Unhandled action type (nil)

(emerald:10703): Wnck-WARNING **: Unhandled action type (nil)

(emerald:10703): Wnck-WARNING **: Unhandled action type (nil)

(emerald:10703): Wnck-WARNING **: Unhandled action type (nil)

(emerald:10703): Wnck-WARNING **: Unhandled action type (nil)

(emerald:10703): Wnck-WARNING **: Unhandled action type (nil)

(emerald:10703): Wnck-WARNING **: Unhandled action type (nil)

```

The number (10703) changes.  I'm currently looking for fixes, and any help would be greatly appreciated.

Thank you.

---

### Post by gsiliceo on 2007-10-16
What graphics card do you guys have?

---

### Post by drinkpepsi on 2007-10-16
Try shutting down compiz and wait for it to load the default theme. Now run compiz again, then apply a theme.

---

### Post by gossrock on 2007-10-16
I can get the same error ("(emerald:20089): Wnck-WARNING **: Unhandled action type (nil)") by opening the compiz config settings manager and unchecking the "windows decorations" check box and then typing "emerald --replace" in a terminal window.  Another thing that happens when I do that though is the borders disappear.  I am currently doing this on Feisty using a third party repository for compiz-fusion.  Check to see if the window decoration checkbox is checked.  I hope that that is your problem since it is a very easy fix.

---

### Post by konungursvia on 2007-10-16
I also have no borders with emerald and beryl, no compiz. The borders disappeared during the upgrade to Gutsy, which I did to restore my sound. That worked, but still no borders, though theme changes do change things like font, scrollbar color, etc.

---

