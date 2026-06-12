---
title: "kwrite popup"
date: 2005-08-06
forum: Desktop Environments
---

### Post by retsel on 2005-08-06
When using the kwrite editor from KDE (not from terminal), before the program loads, I always get an annoying popup that tells me: 

"Will not save configuration, Configuration file 
' /home/..../.../.../config/kwritec' not writable. Please contact your system administrator"          

After I click OK, kwrite seems to operate just fine, but it would be nice to not get the popup, plus I'm concerned that I might actually need to do something to make it right. There's no indication that anything is wrong when I use kwrite in a terminal. Can anyone tell me what I need to do to eliminate this popup? Thanks!

---

### Post by jeffe on 2005-08-06
i can think of two ways to fix this  I'm not a linux expert so i'm not sure 
which one is preferable.

one is sudo rm (config file), then open the program as a regular user, hopefully this will rewrite the file with the correct permissions...

other is sudo chmod u+x (config file)

or something like that...



[QUOTE=retsel]When using the kwrite editor from KDE (not from terminal), before the program loads, I always get an annoying popup that tells me: 

"Will not save configuration, Configuration file 
' /home/..../.../.../config/kwritec' not writable. Please contact your system administrator"          

After I click OK, kwrite seems to operate just fine, but it would be nice to not get the popup, plus I'm concerned that I might actually need to do something to make it right. There's no indication that anything is wrong when I use kwrite in a terminal. Can anyone tell me what I need to do to eliminate this popup? Thanks![/QUOTE]

---

