---
title: "Nautilus Annoyances"
date: 2009-06-01
forum: Desktop Environments
---

### Post by ManDay on 2009-06-01
Hello, some problems with Nautilus:

(1) When I use Nautilus as FTP client it creates an annoying icon on my desktop, which is really not what I want. How can I get rid of it? **[Solved: gconf-editor]**

(2) I'm not able to resize columns as I wish. For instance the "Name"-Column always remains above a certain width. 

(3) Can I somehow change the view to something more Windows-Explorer like? The closest I got is a tree-view in the side panel and a list view in the main-frame. Yet, the main-frame still has something like a redundant tree-view option (I can expand folders in the main-frame, too).

(4) Is there a way to configure what is displayed in "Places"? I don't want to search for files, nor do I want to see "recent documents".

(5) Can I get rid of the "Go" menu and all the history? I'm not interested in my history.

Thanks

PS: Oh and, (6), can I somehow get a level-up (cd ../) shortcut in nautlius?

---

### Post by MadnessRed on 2009-06-01
Regarding 6, beween the forward and stop buttons there is an arrow point up, which says "Up" underneath it, that is your "cd ../" button

Regarding 3, what exactly do you mean, could you be more specific, "Edit" > "Prefernces" > "Views" Tab - "Icon View Defaults", you can select text beside icons, thats a bit more windows like.

---

### Post by ManDay on 2009-06-01
As for (6). I know there is a button in the navigation bar, but since I got latter disabled I wish there would be a "../" file displayed among the directory contents. Is THAT possible?

(3) I just wonder whether the Expand-Arrow next to directories in the main-frame can be disabled.

---

### Post by MadnessRed on 2009-06-01
> **ManDay said:**
> As for (6). I know there is a button in the navigation bar, but since I got latter disabled I wish there would be a "../" file displayed among the directory contents. Is THAT possible?

(3) I just wonder whether the Expand-Arrow next to directories in the main-frame can be disabled.

for the up arrow, only way I can think of would be to make a terminal commands that makes a link to ../ and puts in it every directory, though there is probably a better way.

Also the arrows in the main view can been useful if you are usign the left pain for something else.


edit: you might like thunar
sudo apt-get install thunar

its under accesries, when you run it see if you like it, if you liek it then you can configure it to replace nautilus.

You might like

View > Side Pane > Tree
View location selector > Toolbar

This should do 2,3 and 6 for you.

---

