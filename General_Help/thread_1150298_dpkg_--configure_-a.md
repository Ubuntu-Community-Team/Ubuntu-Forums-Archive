---
title: "dpkg --configure -a?"
date: 2009-05-06
forum: General Help
---

### Post by lopeman1984 on 2009-05-06
this is what i get when i try to update ubuntu.


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


i have no clue what to do.:confused::confused:


i have been using ubuntu on and off for about 2 years...and ive never had this happen to me.


im gonna drown myself if its something so easy to do....

---

### Post by adult swim on 2009-05-06
go to a terminal, applications>accessories>terminal and enter in ```
sudo dpkg --configure -a

sudo apt-get update
``` and it should fix it

---

### Post by lopeman1984 on 2009-05-06
I KNEW IT!!!!!!

I KNEW IT WOULD HAVE BEEN SOMETHING SO STUPID AND EASY AND I JUST WASNT PAYING ATTENTION TO WHAT I WAS TYPING!!!!


thanks a lot guy!

---

