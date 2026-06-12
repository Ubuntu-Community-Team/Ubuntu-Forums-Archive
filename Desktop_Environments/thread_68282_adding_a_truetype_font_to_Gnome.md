---
title: "adding a truetype font to Gnome"
date: 2005-09-22
forum: Desktop Environments
---

### Post by audaz on 2005-09-22
I followed these instructions in the gnome help menu:

To Add a TrueType Font

You can use the file manager to add a TrueType font. To add a TrueType font, perform the following steps:

   1. Open a file manager window and select the TrueType font that you want to add.
   2. From a file browser window, access the fonts:/// location. The fonts are displayed as icons.
   3. Copy the TrueType font file that you want to add to the fonts:/// location. 


When I browse to the fonts:/// location, all of the fonts appear with a little orange lock next to them, and I am unable to add the font I want to this directory (by the way, where is fonts:/// *really* located?).

I don't know if it's a priveledges problem, but I am also unable to do this from a root terminal. 

Any ideas gratefully accepted.

---

### Post by wawa on 2005-09-22
Just copy the fonts to ~/.fonts

Or to /usr/share/fonts to install them system wide

---

### Post by audaz on 2005-09-23
You're the man. Thank you much, worked like a charm.

---

### Post by wawa on 2005-09-23
[QUOTE=audaz]You're the man. Thank you much, worked like a charm.[/QUOTE]                  
         Glad I could help

---

