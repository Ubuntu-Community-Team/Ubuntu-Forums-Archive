---
title: "How to add programs to the applications menu?"
date: 2005-11-29
forum: Desktop Environments
---

### Post by Heavenly Evil on 2005-11-29
[COLOR="Indigo"]I installed kx stitch with synaptic and it hasn't showed up in any of the menus. I don't know where it installs by default, but I would like to have a shortcut in the applications menu. How can I do this?[/COLOR]

---

### Post by cdsboy on 2005-11-29
look at the synaptic name. usualy if you type this in a terminal the program will start. if not search your filesysteme for the files. locate the run file. then enter the run file as a menu thing using systeme tools>Applications Menu Editor

---

### Post by Heavenly Evil on 2005-11-29
[color="Indigo"]I've only used linux for about a week total. How do I know which file is the run file?[/color]

---

### Post by dcstar on 2005-11-29
[QUOTE=Heavenly Evil]I've only used linux for about a week total. How do I know which file is the run file?[/QUOTE]
Synaptic can show you what files are installed by a package, the run files usually exist in a "bin" directory.

If you need to find the whole path for an executable, open a command line and type:

"whereis file-I-want"

and you should get something like "/bin/file-I-want", that is what you put in the properties of your new menu entry.

---

### Post by Heavenly Evil on 2005-11-29
[color="indigo"]Thanks to both of you! It was in /bin/kxstitch. I used the properties tab in synaptic to find the  folder for the icons, and noticed the other file listed there as well.[/color]

---

