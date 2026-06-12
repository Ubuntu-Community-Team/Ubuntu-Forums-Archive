---
title: "how to prevent locking external display when closing notebook's one"
date: 2005-05-08
forum: Desktop Environments
---

### Post by lorap on 2005-05-08
i've an external display connected to my notebook.
once i close my notebook's display the one connected externally closes also.
is there any way to prevent that?
thanks

---

### Post by dave9191 on 2005-05-08
When you close your lid, a shell script is executed. 

/etc/acpi/lid.sh

That in turn calls another script 

/usr/share/acpi-support/screenblank


If you go and edit that file and change the line which says 

su $user -c "(xscreensaver-command -throttle && xscreensaver-command -lock)"

to say 

su $user -c "xscreensaver-command -throttle"

Then it wont lock the screen when you close the lid. 

Dave

---

### Post by lorap on 2005-05-08
dave,thank you very much!
i'll proceed the operations you've predicted as soon as i get home.
dave,is the word "throttle" one of some available options or you just pick any to disable the locking?
thank you again.
pavel

---

### Post by dave9191 on 2005-05-08
The locking is done by  xscreensaver-command -lock 

xscreensaver-command -throttle does something else. You can read up about it in the manual pages of xscreensaver-command (man xscreensaver-command). 

Im using kubuntu and I dont have xscreensaver installed so i can look it up anymore :)

---

### Post by lorap on 2005-05-08
hi dave!
thank you very much!
the information you've granted me was complete.
now i'm able to find the right direction.
thank you very much friend.
pavel

---

### Post by dave9191 on 2005-05-08
No probs :) 

Glad that I could help. 

Dave

---

