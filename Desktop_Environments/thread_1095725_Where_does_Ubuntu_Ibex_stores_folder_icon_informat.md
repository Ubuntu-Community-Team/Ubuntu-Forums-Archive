---
title: "Where does Ubuntu Ibex stores folder icon information?"
date: 2009-03-14
forum: Desktop Environments
---

### Post by Gabix on 2009-03-14
Today, I was making my Ubu look beautiful assigning icons to my different folders and came up with a stupid question. Where does Ubuntu (Intrepid Ibex) stores folder icon information?
I'm the pride owner of two lovely PCs and each have win and ubu running on dual boot. Some folders, like docs, imgs, music and others share the same info and (with windows) the same drive letter (PC1 – U:\imgs PC2 – U:\imgs) (In ubu, the same /media/paritionname). 
So if I set an icon to a folder (PC1\u:\customizedFolder) with win, in its desktop.ini pointing to U:\icos\myico.ico, and the same icon exists in the same location in PC2, when I go to PC2\u:\customizedFolder, the icon is displayed and assigned to that folder without trouble.
In win it's easy to, just copy the desktop.ini from one computer to the other and everything is set up. Or if one of the often reinstallations of win has to happen, I don't lose all that useless configuration of my PCs folders.

Is there a way to do this with ubu? 
Or, Is there a way to assign icons to folders without the usual graphical right click – clicking the folder – looking for the icon – click ok – click ok – click ok?
Basically, Is there an editable “like .ini” file that stores that kind of info? I tried looking in nautilus, but, with my inexperience, I'm quite lost.

Sorry for the uselessness of this thread, but I like to have a nice and ordered machine. :)

PS: And sorry for any spelling horrors you might find, I'm a native spanish talker!

---

### Post by Gabix on 2009-03-14
Maybe I created the thread in the wrong place?

---

### Post by Kevbert on 2009-03-14
The icon files can be found in the /usr/share/icons folder.

---

### Post by Gabix on 2009-03-14
> **Kevbert said:**
> The icon files can be found in the /usr/share/icons folder.

Nice, thanks, but I want the folder icon info...
Example: I create a folder in my desktop like /home/usrName/desktop/myNewFolderWithIcon, I set that folder to have an icon located in /media/myOtherPartition/icons/lalala.png with the simple graphical interface (right click on the new link -> properties -> click to change the default icon -> look for lalala.png in /media/myOtherPartition/ -> click ok -> click ok. Now, that folder has my lalala.png icon setted. Where is the config file located that says after reboot "load lalala.png into /home/usrName/desktop/myNewFolderWithIcon"?

---

### Post by zhocchao on 2009-03-14
i think it's home/.nautilus/metafiles

---

### Post by Gabix on 2009-03-14
> **zhocchao said:**
> i think it's home/.nautilus/metafiles

YES! I think that's it!
I have to do some testing, but I'd say that's the answer.

THANKS!!!!

---

### Post by Gabix on 2009-03-15
Actually, that is the place.
For each folder in my system with icons assigned to it's child folders, there's an xml file with the icon information.
But there is a value that apparently is required and that I can't understand what it means, what it refers, or where to get. The timestamp attribute.

Here's an example of an xml created for a folder named "SuperNani" with 3 customized (with custom icons assigned) folders:

(this file is named "file:%2F%2F%2Fmedia%2FSuperNani.xml"
```

<?xml version="1.0"?>
<directory>
   <file name="Archivos%20grandes%20y%20para%20compartir" timestamp="1235859446" custom_icon="file:///media/Docus/Icos/brown-creature-256x256.png" icon_view_zoom_level="4"/>
   <file name="nani" timestamp="1235859425" custom_icon="file:///media/Docus/Icos/bee.ico"/>
   <file name="GrabarCosas" timestamp="1237088886" custom_icon="file:///media/Docus/Icos/CD-oldSchool.ico"/>
</directory>

```

So, I understand that in "/media/SuperNani" there are 3 folders:
    * "Archivos Grandes y para compartir" with "media/Docus/Icos/brown-creature-256x256.png" icon
    * "nani" with "media/Docus/Icos/bee.ico" icon
and * "GrabarCosas" with "media/Docus/Icos/CD-oldSchool.ico" icon
But, where do I get that "timestamp" attribute?

I tryed creating a new value "by hand" assigning the folder name and the new icon location but that timestamp value seams to be needed.

Any ideas?

---

### Post by Stratis on 2009-03-19
> **Gabix said:**
> 
I tryed creating a new value "by hand" assigning the folder name and the new icon location but that timestamp value seams to be needed.

Any ideas?

The usual graphical right click – clicking the folder – looking for the icon – click ok – click ok – click ok.

; )

Cheers

---

