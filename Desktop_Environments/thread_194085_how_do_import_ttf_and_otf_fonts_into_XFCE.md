---
title: "how do import ttf and otf fonts into XFCE ?"
date: 2006-06-10
forum: Desktop Environments
---

### Post by TOPPEL on 2006-06-10
:-k 

hewlp !

how do import ttf and otf fonts into XFCE ?

---

### Post by henriquemaia on 2006-07-06
Hi again,

You just have to drop the fonts you want to install in the folder:

~/.fonts

If that folder doesn't exist, create it:

```
cd
mkdir .fonts

``` 
Then open that folder on nautilus (or othe file manager of your choice) and drop the fonts there. Close the applications where you're going to use the newly installed fonts and reopen them (if they were open in the first place - restart X if necessary).

Hope this helps (this did the trick to me).

---

### Post by TOPPEL on 2006-07-07
Thank you.  

That however is a user setting and not a global one.  when you open fonts:///

that points to the location of the important global fonts or -- where you import fonts.  people have told me to gksudo nautilus but its not always a sure shot for me.  

i do appreciate your assistance though and for a single person workstation it works just fine.

---

