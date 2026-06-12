---
title: "help with smtp"
date: 2009-03-10
forum: General Help
---

### Post by shanab on 2009-03-10
hello everyone
i have just changed to ubuntu and i was trying to set up my mail on evolution 
but the mail provider i am using is 1and1.com and the smtp port is not the usual one (port 25) but i use (port 587) instead on microsoft outlook and i cannot send any mail now i have been searching for a way to change the smtp port but i cannot find it please help

---

### Post by pyrofreek_9 on 2009-03-10
try adding :587 to the end of the server name. For example if the server is smtp.1and1.com, make it smtp.1and1.com:587

---

### Post by shanab on 2009-03-10
thank you for your reply but i tried the proposed solution and it didn't work and it said 

"host look up failed: smtp.1and1.com: name or service not known"

---

### Post by hub_cap on 2009-03-10
> **shanab said:**
> thank you for your reply but i tried the proposed solution and it didn't work and it said 

"host look up failed: smtp.1and1.com: name or service not known"

I was having the same problem and the fix worked for me.
smtp.comcast.net:**587**:D

---

### Post by mebomechanicno1 on 2010-07-14
> **shanab said:**
> thank you for your reply but i tried the proposed solution and it didn't work and it said 
 
"host look up failed: smtp.1and1.com: name or service not known"
 
This is exactly the same problem I have been having; did you ever get it fixed?

---

### Post by dcstar on 2010-07-14
> **mebomechanicno1 said:**
> This is exactly the same problem I have been having; did you ever get it fixed?

Any solution is obvious, do **not** use the example given as that poster guessed what the SMTP server **might** be, use the **actual** DNS name of what it is.

---

