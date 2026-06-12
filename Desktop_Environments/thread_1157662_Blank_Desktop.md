---
title: "Blank Desktop"
date: 2009-05-12
forum: Desktop Environments
---

### Post by blarney on 2009-05-12
I have a blank desktop.  I was getting en error message that said :
"users $home/.dmrc file is being ignored. this prevents the default session and language from being saved period. file should be owned by user and have 644 permission. users $home directory must be owned by user and not writeable by other users"

I followed the instructions and finally got rid of the error messages thanks to a budy of mine.  Now I just get a blank desktop though.  I am new to all this and it has been one serious struggle.  Can anyone tell me why my desktop is blank with just a cursor and a background?

---

### Post by andrea000 on 2009-05-12
I don't know why but try hitting alt+f2 and typing gnome-terminal in the run box then in the terminal put 
startx.I dont know if that will work but you will know if x is just not starting or if you need to reinstall.

---

### Post by blarney on 2009-05-13
The alt + F2 does absolutely nothing.  

Nothing works on the desktop.  I can go into it just find and run command line though and it all seems fine just no desktop on it.

---

### Post by andrea000 on 2009-05-13
Ok if you can get to the terminal try this

Enter
chmod 644 .dmrc
chmod 700 ~

or if all else fails reinstall the desktop

sudo apt get install ubuntu desktop-reinstall

or just for a install

sudo apt get install ubuntu desktop

---

