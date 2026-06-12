---
title: "How to use kate in SU mode in the terminal"
date: 2009-01-01
forum: Desktop Environments
---

### Post by tropdoug on 2009-01-01
Sincle migrating a few days ago to Kubuntu 8.10 to givw KDE a try I have been frustrated in that using a terminal I could not get Kate (the advanced text editor) to open as 'root' to be able to edit and save config files like /etc/fstab

I finally found out what to do just now, and thought others might be having the same problem. 

the command to use is simply -- ```
kdesudo kate */filename*
``` various old posts suggest other commands like sudo su but they did not work. this one did, and now I am a happy camper again. 

Hope this helps someone
(by the way I use yakuake - a dropdown terminal emulator -- BRILLIANT!)

---

