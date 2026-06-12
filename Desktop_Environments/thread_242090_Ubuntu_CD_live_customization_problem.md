---
title: "Ubuntu CD live customization problem"
date: 2006-08-23
forum: Desktop Environments
---

### Post by Yann_K on 2006-08-23
Ubuntu's customization problem 

--------------------------------------------------------------------------------

Hello guys,  

I create a personnal Ubuntu "Dapper" CD Live.
But at the Ubuntu start session, I meet the error message below :

"user $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permission. User's $HOME directory must be owned by user and not writable by another users"

I tried to search unsuccessfully the '.dmrc' file on my temporary Ubuntu's custom folder (like specified on [https://help.ubuntu.com/community/Li...omization/6.06](https://help.ubuntu.com/community/Li...omization/6.06)) to change file's permission (chmod 644 ~/.dmrc and sudo chown my_login /home/my_login/.dmrc then chmod 700 /home/my_login )
But this file is present on my local Ubuntu system (HDD).

What can I do ?  

Many thanks !

---

