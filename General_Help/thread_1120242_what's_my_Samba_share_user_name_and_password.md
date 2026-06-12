---
title: "what's my Samba share user name and password?"
date: 2009-04-08
forum: General Help
---

### Post by anon0 on 2009-04-08
[SOLVED]

I'm booting off live USB and when I try to access Ubuntu's shared drive from Windows I am asked the user name and password, which I believe were not entered initially. How should I set up the user name and password so I can access the shared data?

I think the password is set up by smbpasswd but how do you get a user name?

...ok got it: 
# adduser USERNAME
# smbpasswd -a USERNAME

---

