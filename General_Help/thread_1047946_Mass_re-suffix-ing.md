---
title: "Mass re-suffix-ing"
date: 2009-01-22
forum: General Help
---

### Post by codeking on 2009-01-22
I ripped some CDs in the OGG format.  Unfortunately, they saved as .oga, not .ogg, so they aren't picked up by my Windows XP music player (MediaMonkey).  Is there a way I can rename all the .oga songs to .ogg?

---

### Post by Def13b on 2009-01-22
I'm no expert so perhaps my method isn't the best but I recently had a very similar issue and needed to change the extension of my oga files to ogg.

I used the rename command as below, simply navigate to the folder with the files you want to rename and type:

rename s/\.oga$/.ogg/ *.oga

Also, if I'm using this command wrong feel free to correct me as I'm not sure why or how this one works, just kind of tried copying/modifying what  I read in "man rename".

---

### Post by codeking on 2009-01-25
It all work, I just had to do a small edit to make it work in all my subdirectories.

---

