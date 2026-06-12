---
title: "Evolution Never Asks For Password"
date: 2006-10-02
forum: Desktop Environments
---

### Post by genek6 on 2006-10-02
This is my first Ubuntu install, I installed Dapper..

I'm trying to set up Evolution for a pop mail account.

It never asks me to put in a password even though I have "password" checked as the "Authentication" type.

Any simple solution...

---

### Post by henriquemaia on 2006-10-02
What type of encryption are you using? Try simple.

---

### Post by genek6 on 2006-10-03
Wow! I got it figured out. There were two errors.

_Under POP Mail I had the server as:_

pop.isp.xxx

_It needed to be_ 

mail.isp.xxx

_The Authentication needed to be:_
Use Secure Connection Whenever Possible

_Authentication Type:_
Password

Now Evolution asks for a password and connects to my POP account with no problem...

---

