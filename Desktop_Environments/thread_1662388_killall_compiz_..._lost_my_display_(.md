---
title: "killall compiz ... lost my display :("
date: 2011-01-08
forum: Desktop Environments
---

### Post by afizs on 2011-01-08
Hi...!!

in terminal I typed the command

killall compiz 

after this i lost everything. after the reboot i am getting only terminal mode 

even I tried startx command .......... 

plz help me out............ 

thanks in advance.

---

### Post by afizs on 2011-01-08
what is killall compiz command. 

I typed this command, and I lost my display 

when i reboot the system i got nothing except black screen plz help me

---

### Post by Krytarik on 2011-01-08
"killall compiz" -as the words suggest- kills the process of Compiz, the window manager.

This should only affect the current session.

Does Ubuntu boot up and then goes black or immediately after choosing it in the boot menu? Do you mean blinking cursor?

The "recovery mode" at the boot menu should bring you to the desktop or at least a console.

---

### Post by afizs on 2011-01-08
thanks for your answer

I got blinking cursor .......... when i restart the system i got only terminal........ 

I typed startx command it didn't give me display

---

### Post by realzippy on 2011-01-08
..have you run an update,installed/uninstalled anything *before* you have run "killall compiz" (..which indeed cannot do any permanent harm/damage X server)?

---

