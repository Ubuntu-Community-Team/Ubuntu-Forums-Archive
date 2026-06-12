---
title: "ubuntu refuses to let me reinstall a theme of mine"
date: 2009-06-03
forum: General Help
---

### Post by Meow27 on 2009-06-03
ok so there is this theme "TechniX1" 

i like it alot, but after installing a iconset, ubuntu went haywire and a bunch of main processes just crashed. so i removed it, and techix1, but when i try to reinstall it, i get this message 
"Installation for theme "TechniX1" failed.
Can't recursively copy directory"

this is getting so frustrating for me. i hate having to reinstall ubuntu for something so lousy as this. all of the other themes look like crap on my laptop and this one was one i really liked

can someone please help me? im posting in this board cause its the only one people reply to :(

disclaimer: the theme isnt actually mine, i was just using a figure of speech in the title

---

### Post by Meow27 on 2009-06-04
humpty  bumpdy

---

### Post by Megrimn on 2009-06-05
Could you post a copy of the theme's tar.gz file?  I can try it and see if I get the same results.  

The other thing you could try doing in the meantime is acquiring a new copy of the same theme and try installing that.  

Another option is to extract the theme from the tar.gz file, rename the folder to something other than "TechniX1", like "Pain_In_The_Butt" or something, and make a new tar.gz file from that (easy, just right-click and hit "create archive").  Then install that file and see what happens.

---

### Post by Meow27 on 2009-06-05
> **Megrimn said:**
> Could you post a copy of the theme's tar.gz file?  I can try it and see if I get the same results.  

The other thing you could try doing in the meantime is acquiring a new copy of the same theme and try installing that.  

Another option is to extract the theme from the tar.gz file, rename the folder to something other than "TechniX1", like "Pain_In_The_Butt" or something, and make a new tar.gz file from that (easy, just right-click and hit "create archive").  Then install that file and see what happens.

[http://www.gnome-look.org/content/show.php/TechniX?content=79463](http://www.gnome-look.org/content/show.php/TechniX?content=79463)
this was the iconset [http://www.gnome-look.org/content/show.php/Titanium?content=75038](http://www.gnome-look.org/content/show.php/Titanium?content=75038) don't use it with jaunty :/

renaming the folder gives the same error message (when installing the theme)

---

### Post by Megrimn on 2009-06-05
Ok, try this.

-go into your home folder, the one named after you.
-hit "ctrl-h", and the hidden files will appear.
-navigate to the folder ".themes"
-delete the folder named "Technix"

-from your home folder again, hit "ctrl-h" and navigate to the folder ".icons"
-delete the folder named "Titanium."

Try reinstalling the theme again... if my hunch is right, this should work...

---

### Post by Meow27 on 2009-06-05
i followed your guide (thanks for telling me about the icons folder, i didnt know about that one (knew about .themes)) 

well now that titanium is gone, network manager doesn't crash when i try to use technix, problem now is, is that i had to remove technix again since it wasn't showing its gtk theme (blank gtk) so i removed it from themes and its giving me the same error message as it did the first time.

its not on the appearance menu, .themes, or .icons

......:/
----------------------------------
edit it worked the 5th time for some reason :/

---

### Post by Megrimn on 2009-06-05
> **Meow27 said:**
> 
edit it worked the 5th time for some reason :/

Hooray, glad that worked out. :)

---

