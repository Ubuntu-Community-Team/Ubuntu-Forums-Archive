---
title: "VMware guest cannot see host"
date: 2007-03-14
forum: Desktop Environments
---

### Post by frankiethepill on 2007-03-14
Using WinXP as guest on VMware - cannot get access to host drives. The hosts are all shared with smb and I can see an icon in Windows file explorer but I need a name and  password to access- I don't do passwords unless compulsory and only use the same one if necessary, together with one user name on any system- no combination of password or username will work - is there anyway of finding out what password is required? (defeats the object of passwords I know, but I think there are various config  files which may have some bearing on this)

I see talk of using ssh as some say it is better- any howtos available for this?

---

### Post by scxtt on 2007-03-14
on ubuntu host, do:

smbpasswd -a $USERNAME

then use that username and password from windows ... you may need to preface it w/ sudo ...

---

### Post by frankiethepill on 2007-03-14
Thank you -worked like a charm! Has ended so much grief.
Also thank you for the prompt reply
Regards Francis

---

