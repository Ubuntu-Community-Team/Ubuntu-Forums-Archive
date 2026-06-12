---
title: "xtail"
date: 2006-01-31
forum: Desktop Environments
---

### Post by acehigh on 2006-01-31
I would really like a 'tail -f' program but with graphical interface.
I know the xtail one, but is a terminal program... 
Does someone know if there is a program that does the job?

many thanks

---

### Post by kaamos on 2006-01-31
Just came up with this. :) 

Say the file you are trying to tail is /var/log/messages
```
tail -f /var/log/messages | zenity --list --title "Messages" --text "Here is the output of /var/log/messages.." --column "Entrys" --width=600 --height=600
```
You must have the zenity package installed.

---

### Post by acehigh on 2006-02-09
Thanks... Zenity is a nice package...I tried it using the --list option (as your suggestion) and it doesn't follow the tail of the file... I have to use the scroll bars to reach the end. Am I doing something wrong?

---

