---
title: "setting path permanently"
date: 2006-08-25
forum: Desktop Environments
---

### Post by christoforever on 2006-08-25
ok so say i want to set a path for /home/documents/bin

how do i do this, so its permanent,as in every time i start ubuntu over the path will still be set. Pardon my ignorance if this sounds like a noob question, but im recently new to the whole linux thing.

sincerely,
Chris

---

### Post by scxtt on 2006-08-25
put this is ~/.bashrc:

PATH="${PATH}":/home/documents/bin
export PATH

---

### Post by christoforever on 2006-08-25
ok i see about three lines of code. what im getting is at the command line type: PATH="${PATH}":/home/documents/bin

and this will work?

what is the export path for?
   
and what is put this is ~/.bashrc:    for ?

---

### Post by scxtt on 2006-08-25
there are 2 lines of "code" (in bold) which need to be added to a file:

[B]PATH="${PATH}":/home/documents/bin
export PATH[/B]

you'll edit a file called **.bashrc** in your home directory (~) and add those lines so that any time you invoke bash, PATH will be updated ... export PATH is used so that your system is aware of the change ...

---

### Post by christoforever on 2006-08-25
i c thanks for clearing that up.

Sincerely,
Chris

---

### Post by christoforever on 2006-08-25
ok so i put that exact code at the bottom of the basrc file, and it seems to work. now if i want to set another path to another directory do i just repeat the same process, but with a different directory? I did just that and it worked, but im wondering if this is the proper way in which to do it?

---

### Post by scxtt on 2006-08-25
you'll just tack it onto the end of the one you added initially, so if you want to add /home/user/ADD_TO_PATH, you'll just edit the entry from above to:

**PATH="${PATH}":/home/documents/bin:/home/user/ADD_TO_PATH**

---

### Post by christoforever on 2006-08-25
hey thanks alot for help. its greatly appreciated.

---

