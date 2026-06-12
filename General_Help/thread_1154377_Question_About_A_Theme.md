---
title: "Question About A Theme"
date: 2009-05-09
forum: General Help
---

### Post by izizzle on 2009-05-09
So, I downloaded [THIS]("http://www.gnome-look.org/content/show.php/Mira?content=89831") theme, but I need help on installing it. It says it works with GTK 2.x, but all I can find are emerald packages. I really want to install this theme because it goes perfectly with the rest of my setup.

Thanks.

---

### Post by Tipped OuT on 2009-05-09
Go to Synaptic Package Manager (System< Admin< Synaptic Package Manager). Search for "emerald". Download and install. Hold ALT+F2. Type in the run box "emerald --replace". Now you're using Emerald. Go to System< Preferences< Emerald Theme Manager to install your theme.

---

### Post by geirha on 2009-05-09
I had a look at the theme. Seems it contains themes for both GTK and emerald. Now, the typical way to install a GTK theme is to open System -> Preferences -> Appearance, then drag the archive containing the theme over to the apperance window. 

There is a catch though. It only accepts gzipped tar archives (.tar.gz), but the archive you download from that site is only a tar (.tar). Easiest way to get around that is to open the tar archive in the archive manager, choose Archive -> Save as from the menu, and add a .gz at the end of the filename (Also make sure Archive type at the bottom is set to Automatic). 

Drag the Mira_by_sen7.tar.gz file over to the Apperance window and the new theme should be available in the selection.

---

### Post by ad_267 on 2009-05-09
Untar the archive and copy both the mira and mira2 directories into ~/.themes. The metacity and GTK themes are all there, they just aren't in separate .tar.gz archives from the emerald themes.

---

### Post by Tipped OuT on 2009-05-09
^^ Thanks for the back up help guys ^^ :redface:

---

### Post by izizzle on 2009-05-09
Thanks geirha. Your method worked! I love this theme....

Thanks to all who replied as well!

---

