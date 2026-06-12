---
title: "Connect to server won't send ssh password"
date: 2008-10-01
forum: Desktop Environments
---

### Post by KDB9000 on 2008-10-01
I was trying to connect to a system using SSH so I could transfer some files to it, but when it asked for the password it wouldn't send it. I type the password in (correctly) and it just keeps asking me for the password. I have this same problem when I was trying to do SSH to another system in the terminal. It would just keep asking me for the password even though I typed it right. What could be wrong?

---

### Post by KDB9000 on 2008-10-07
I just found out that the Putty keys aren't the same as OpenSSH keys. That was my problem. WinSCP and Putty must be able to work with the same keys, but you need OpenSSH generated keys for everything else.

---

