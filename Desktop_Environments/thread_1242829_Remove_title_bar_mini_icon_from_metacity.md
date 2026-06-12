---
title: "Remove title bar mini icon from metacity"
date: 2009-08-17
forum: Desktop Environments
---

### Post by Syrinx Priest on 2009-08-17
Hi, I set a new metacity theme (plastique3) and it has the icon of the app in the titlebar, how do I remove this? (xml editing)

---

### Post by Syrinx Priest on 2009-08-17
Before going out bump.

---

### Post by asmoore82 on 2009-08-17
```
gconf-editor
```
and edit the key /apps/metacity/general/button_layout.

maybe to be ":minimize,maximize,close"

---

### Post by Syrinx Priest on 2009-08-17
No, that removes the actual menu button, I mean the icon of the Application (ex. Firefox, Terminal, etc.) next to the text.

---

### Post by eamon63 on 2009-08-18
In metacoty theme xml file, look for this line

<draw_ops name="title-text-focused">   
and
<draw_ops name="title-text-unfocused">

under each line are items   <clip...    and    <icon...
remove/comment out these so that you'll only have 
<title color=...

i think you also need to remove/comment out
<constant name="IconSpacing".../>

---

### Post by Syrinx Priest on 2009-08-18
That did it, thank you very much!

---

