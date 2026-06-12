---
title: "scite: doubleclick to open files doesn't work"
date: 2005-10-28
forum: Desktop Environments
---

### Post by Jonne on 2005-10-28
If I set in Nautilus to open a certain file in scite, it will not open it.

It will open scite, and i'll see in the title bar this path:
/home/jonne/file:/home/jonne/file.txt
(example, with file.txt being in my home directory)

Now, the solution is probably to tell nautilus (or scite) to just open /home/jonne/file.txt , but I can't find a config file/dialog to open it.

It works from command line, so i suspect nautilus is at fault here.

---

### Post by Jonne on 2005-11-07
<bump>

---

### Post by stilus on 2005-11-11
I used scite (which, I am starting to find out, is an amazing (fully GTK+) code editor) to open a .css file. Next thing to do is right-click > properties > Open With and select scite (If it isn't already there). css is now being opened with scite. You could do that to all the file types you'd want to edit in scite. 
I've been playing with scite for a little now cause I saw it being praised to high heavens here an there... and now I'm starting to feel the urge to write a rave (mini) review too! 
[LIST=1]
[*]nice thing: you can edit the scite config files (given the right permissions) directly in scite. 
[*]nice thing: integrated grep
[*]nice thing: light on its feet and easy to use and navigate.
[*]nice thing: toolbar.usestockicons=1 <- there's your scite fully integrated into your own gnome look and feel (see Global.properties)
[*]nice thing: try it, its free!
[/LIST]
I'm off to go and be all pleased and enthousiastic with this great code editor! :D

---

### Post by Jonne on 2005-11-11
Well, i managed to fix my problems with opening the file (just set the 'open with' settings again, through rightclick>properties). Nautilus' open file settings are still a mess, though, but I'll manage.

I want to use Scite because I use Notepad++ in Windows, and Scite is its Linux nephew, or brother, or whatever (they're related somehow ;) ). I just love the editor, It really works well for editing html, php, css, etc...

---

### Post by Sykil on 2005-11-11
Slightly offtopic:  SciTE and Notepad++ are based on the Scintilla editing componet.  SciTE was made by the Scintilla guys to demonstrate its features, but it evolved into a more feature-complete text-editor.

---

### Post by kwisatz on 2005-11-16
I have the same annoying problem of Jonne, if I click on a file associated with scite on nautilus, scite starts but it try to open /home/myhome/file://PATH/TO/OPENED/FILE...

---

### Post by Demosthenes on 2005-11-18
I think i have a solution for this, it was an issue that was bothering me also.

When you add scite as an application to open with; instead of choosing scite from the list choose custom command and type: ```
scite -open:
```
you should now be able to open with scite.
(You can also type "scite " [scite(space)] in the custom command box that seems to work too, which is what is in the command when you choose it from the list so i have no idea why that doesn't work)

---

### Post by trib4lmaniac on 2006-03-11
Editing SciTE's application menu entry by taking off the %U parameter seems to fix the problem. I am not sure what %U does, but SciTE's behaving.

---

