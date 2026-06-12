---
title: "Some Compiz Questions"
date: 2006-09-04
forum: Desktop Environments
---

### Post by PathSpace on 2006-09-04
First off, is there any way to change the graphic on the top and bottom of the cube...something to replace the white square with "Novell" written in it?

Also, I have /usr/bin/compiz-start in my Sessions-->Startup Programs, but it does nothing; I have to run that command manually.  :-k   Any ideas about either of these annoyances?  :rolleyes: :-D 

Otherwise...GREAT JOB, Quinn!!  :mrgreen: :mrgreen:

---

### Post by Dr. Nick on 2006-09-05
gset-compiz used to change the pictures, i think its obselete now. poke around in gconf-editor and you may find it.


Did you set the executable +x to compiz-start?

I am actaully having issues with it now where cgwd isnt working, so until I get that fixed im without it.

---

### Post by Saibot on 2006-09-05
If your compiz is up-to-date you'll have to use CSM to change the pictures on the cube.  Just type CSM in a terminal and go to 'Desktop Cube' on the side and then the 'String Lists'.

---

### Post by PathSpace on 2006-09-05
> **Saibot said:**
> If your compiz is up-to-date you'll have to use CSM to change the pictures on the cube.  Just type CSM in a terminal and go to 'Desktop Cube' on the side and then the 'String Lists'.

I changed the image there in csm, but it has no effect.  :-k

---

### Post by Dinerty on 2006-09-05
> **PathSpace said:**
> I changed the image there in csm, but it has no effect.  :-k

The image can only be PNG I believe.

go to "Desktop cube" > "Option toggles" tick "Scale image on top" and "Scale image on bottom" then go to "String lists" and add your .png pictures in there

---

### Post by PathSpace on 2006-09-05
I just did exactly what Dinerty said, using a .png image.  It shows up in the strings list in the appropriate section of csm, but the Novell image still shows up in the cube.  And compiz doesn't automatically start still, even though I put /usr/bin/compiz-start in my Startup Programs under Sessions.  :confused:

---

### Post by Dr. Nick on 2006-09-05
Make it compiz-start.py instead and see how that works, Mine wasnt happy without the .py

---

### Post by Dinerty on 2006-09-05
> **PathSpace said:**
> I just did exactly what Dinerty said, using a .png image.  It shows up in the strings list in the appropriate section of csm, but the Novell image still shows up in the cube.  And compiz doesn't automatically start still, even though I put /usr/bin/compiz-start in my Startup Programs under Sessions.  :confused:

you need to delete the "novel.png" from the top/bottom image list, else it will use that, even though you speicifed another image.

---

### Post by ayoli on 2006-09-05
> **PathSpace said:**
> I just did exactly what Dinerty said, using a .png image.  It shows up in the strings list in the appropriate section of csm, but the Novell image still shows up in the cube.  And compiz doesn't automatically start still, even though I put /usr/bin/compiz-start in my Startup Programs under Sessions.  :confused:
did you remove novell.png from csm/desktop cube/string list ?
did ou add your image with full path ?

---

### Post by PathSpace on 2006-09-05
OK, I got the cube top/bottom images working now by deleting the Novell image from the Strings List.  :)

But Compiz *still* doesn't start up automatically, even though I changed it to /usr/bin/compiz-start.py in the Startup Programs.  :-k

---

### Post by diggity on 2006-09-05
I tried using the full path and it never worked. The solution I found was to simply put the .png image into the same directory as the novell.png image (same for the skydome if you want to change that image) and it worked. I didn't have to use the full path in the editor.

---

### Post by ayoli on 2006-09-05
> **PathSpace said:**
> OK, I got the cube top/bottom images working now by deleting the Novell image from the Strings List.  :)

But Compiz *still* doesn't start up automatically, even though I changed it to /usr/bin/compiz-start.py in the Startup Programs.  :-k

just put **compiz-start** (without .py) in starup programs and remove other compiz entries here if any

---

### Post by ayoli on 2006-09-05
> **diggity said:**
> I tried using the full path and it never worked. The solution I found was to simply put the .png image into the same directory as the novell.png image (same for the skydome if you want to change that image) and it worked. I didn't have to use the full path in the editor.

full path for toppand bottom images in csm works fine for me.

---

### Post by PathSpace on 2006-09-05
> **ayoli said:**
> just put **compiz-start** (without .py) in starup programs and remove other compiz entries here if any

For some reason, I cannot remove the other compiz entry (which is compiz-tray-icon), because "disable" is grayed out.  But I can disable it, which works great.  Thanks.  :D

---

### Post by ayoli on 2006-09-05
> **PathSpace said:**
> For some reason, I cannot remove the other compiz entry (which is compiz-tray-icon), because "disable" is grayed out.  But I can disable it, which works great.  Thanks.  :D

i didnt remove it i've edited to replace compiz-tray-icon with compiz-start :)

---

### Post by PathSpace on 2006-09-05
> **ayoli said:**
> i didnt remove it i've edited to replace compiz-tray-icon with compiz-start :)

Good idea.  :D

---

