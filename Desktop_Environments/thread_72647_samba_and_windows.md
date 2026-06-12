---
title: "samba and windows"
date: 2005-10-06
forum: Desktop Environments
---

### Post by DarkManX4lf on 2005-10-06
ok i have installed smb and smbfs and i got folders in linux shared and setup, i can access these folders using my xbox perefectly fine and it doesnt ask me for a login or a pw ( yes its modded ), but in windows when i try to access these shared folders it asks me for a password and a login....how do i get rid of that? or what isthe login?

---

### Post by Corvillus on 2005-10-06
I think you have to use
```
sudo smbpasswd -a username
```
to add an account to samba (by default, there are no accounts configured)

---

### Post by DarkManX4lf on 2005-10-09
thanks that worked

---

