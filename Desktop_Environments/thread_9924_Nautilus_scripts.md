---
title: "Nautilus scripts"
date: 2005-01-02
forum: Desktop Environments
---

### Post by Quest-Master on 2005-01-02
I downloaded a script from [http://g-scripts.sf.net](http://g-scripts.sf.net), and placed it in the standard directory: /home/qmaster/.gnome/nautilus-scripts

However, the script doesn't show up when I right click anywhere. Does anyone know where Nautilus scripts are put in Ubuntu?

---

### Post by EdCrypt on 2005-01-02
[QUOTE=Quest-Master]I downloaded a script from [http://g-scripts.sf.net](http://g-scripts.sf.net), and placed it in the standard directory: /home/qmaster/.gnome/nautilus-scripts

However, the script doesn't show up when I right click anywhere. Does anyone know where Nautilus scripts are put in Ubuntu?[/QUOTE]
Maybe ~/.gnome2/nautilus-scripts

---

### Post by Rancoras on 2005-01-02
This page will answer that question and it has a bunch more useful scripts.

[http://www.ubuntulinux.org/wiki/NautilusScriptsHowto/view?searchterm=scripts](http://www.ubuntulinux.org/wiki/NautilusScriptsHowto/view?searchterm=scripts)

---

### Post by Quest-Master on 2005-01-03
Ah, I found the problem. There has to be ANOTHER directory inside nautilus-scripts for any of the scripts to show up.

So, nautilus-scripts/open-terminal-here won't work but nautilus-scripts/terminal/open will work. Odd.

---

### Post by poptones on 2005-01-03
What? Are you using warty?

Put the script in "scripts." Mark it executable. If you don't make it executable it won't show up.

Works just fine in warty. Can't say about hoary.

---

