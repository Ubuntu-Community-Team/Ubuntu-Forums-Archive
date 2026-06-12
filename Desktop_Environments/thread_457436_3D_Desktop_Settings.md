---
title: "3D Desktop Settings"
date: 2007-05-28
forum: Desktop Environments
---

### Post by nami on 2007-05-28
I have managed to get the 3d dekstop working from the built in desktop effects in 7.04, but its not how it used to be with berly.  in berly it used to rotate as 1 bit desktop in twinview mode, but look what happens here...

for some reason its displaying 2 cubes...

how do i get 1 big cube.

i used the following commands to get the cube working in the first place:

gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 2
gconftool-2 --type int --set /apps/compiz/general/screen0/options/number_of_desktops 4

is there an option to get 1 big desktop cube?

---

### Post by satellite360 on 2007-06-11
I guess this would work:
gconftool-2 --type int --set /apps/compiz/general/screen0/options/hsize 4
gconftool-2 --type int --set /apps/compiz/general/screen0/options/number_of_desktops 1

---

### Post by 6kutijs on 2007-06-14
hey guys I have a question ... how do I switch to the 3D cube view???

---

### Post by VAsHachiRoku on 2007-08-13
Ctrl+Alt+(Mouse-Hold-Left Click)

Move the mouse to move the cube.

---

### Post by matthiasfan on 2007-08-13
Not to hijack, but it follows the same question and I don't want to start a new thread.  I am new to Ubuntu, and I activated the 3d effects.  I try the ctrl+alt+left mouse button and nothing happens.  The mouse is just trying to highlight.  Can someone please point me in the right direction?  I have read some on the configuration editor, but I do not really want to make things worse than they already are.

Thanks.

---

### Post by bjarneh on 2007-08-13
if you're using compiz + ubuntu (Gnome) then 

$ gnome-compiz-preferences 

should give you the configuration tool....

---

### Post by matthiasfan on 2007-08-13
I saw the configuration tool, but I don't understand why the ctrl+alt+left mouse button isn't working.  Is it something in the configuration editor that I have to change in order for this to work?

---

### Post by jaffa_nz on 2007-08-14
i had same problem.  it turned out that off the bat, i had wobbly windows but no cube or no "flipping" it around.  I had to enable the number of desktops, ie set them from 1 to 4.  And i had a cube.

you've probably already solved this.

---

