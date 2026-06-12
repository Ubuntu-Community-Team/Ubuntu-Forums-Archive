---
title: "tsclient not saving password"
date: 2006-09-06
forum: Desktop Environments
---

### Post by itsdaveperdue on 2006-09-06
Hey Everyone,

I've got an issue with tsclient(v0.140) in Dapper...it's not saving any passwords.  I'm using it to connect to some Windows systems with RDP.  If I type in the password and hit connect it doesn't use the password.  It will connect and give me the Windows login dialog.

I've used rdesktop by itself:
```
rdesktop -u Admin -p PaSSWord
```
And it works great.

If I edit the .rdp file manually and put the password in there:
```
password:b:PaSSWord
```
It will work fine.

Any Ideas of how I can get tsclient to save or use the passwords?

P.S.: I've checked the change log for the new tsclient .148 but it doesn't say anything about this problem.

Thanks,
Dave.

---

### Post by z600 on 2007-02-10
Hi, 

I'm having the same problem. Even though I enter a password into the tsclient to remote desktop into a windows box, the password is never used. Upon connecting to the windows box, the password is requested again. Is there anyway to save this password in a .rdp file?

---

