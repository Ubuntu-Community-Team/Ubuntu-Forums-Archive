---
title: "Cursors wont work"
date: 2008-12-04
forum: Desktop Environments
---

### Post by jairom70 on 2008-12-04
Ok im using command emerald --replace

i right clikc my Desktop and go to 
"Change Desktop Background"-->"Themes"-->"Custumize"-->"Pointer" 

I do not see the pointer i Xtracted into the Themes tab. I go to 
Home/User/.Themes  and the folder i downloaded and Xtracted is there. but not in the list..i have logged out and back in.. i have restarted, still nuttin. I delete the folder from .themes folder and drop it back in the Themes Tab. and it tells me "Can't move directory over directory"

when i try to  choose any of the original pointers in the list . they work. but only when i open firefox browser. when i move the pointer outside the firefox window it goes back to default. when i move the pointer back to firefox window i see the one i selected from the original menu list.  

what am i doing wrong?

---

### Post by jairom70 on 2008-12-04
OK so i figured out it said "Cant move directory over directory" because it makes a copy of the cursor folder in the .icons folder and i need to delete it from there as well before i reinnstall it. 

I am still having the problem of the cursors i choose only showing up on the Firefox window and the reverting back to the default cursor when i move the pointer out of the Firefox window. I am only able to see my new cursor on the FireFox window.
 
If I Open a regular window. like my Documnets. i still see the default cursor.

---

### Post by heartwarmer on 2009-03-05
I have the same problem, yesterday i did a clean 8.10 install.
I tried copying/moving the folder to /usr/share/icons but it didnt help,
i even moved the default cursors away but it didnt help either.
now i have 2 cursers,one works with firefox,pidgin screenlet(but not with pidgin) and one with the rest..!!

---

### Post by damis648 on 2009-03-05
Once the cursor theme is installed, click "Customize" in the themes tab and then click the "Pointer" tab. Select the one you want, and take note of the exact name. Then open ccsm and go to 'General' and where it says 'Cursor Theme' put the name of the cursor theme you are using and press enter.

---

### Post by heartwarmer on 2009-03-05
Wow, I dont know how i forgot this!! thankss :D

---

