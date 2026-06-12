---
title: "Transferring Hosting including mail tutorial ?"
date: 2020-03-07
forum: Desktop Environments
---

### Post by dbee on 2020-03-07
I'm going to transferring hosting from one web host to another. I'll also be transferring the mail in the respective accounts using thunderbird if possible.

Are there any good tutorials for doing this ? I don't want to mess up so a comprehensive tutorial is a must.

Thanks :-)

PS: my host says that if i set up the new webspace and activate mail hosting it could interefere with the present email on the 'real' account. How does this happen exactly ? 
Surely once the dns records aren't altered, then the mails should find their way 'home' ?

---

### Post by TheFu on 2020-03-07
Control the priority for where SMTP connections happen by the MX record priority.
Get everything setup on the new host, just have a higher MX priority, until you are ready to switch, then swap the DNS MX record priorities so the new provider gets email.

If you bought an all-in-one domain+hosting+email package, you might not have this level of control.  I keep the Registrar, DNS and all servers on separate providers to avoid that problem.

As for a "comprehensive tutorial", sorry. Cannot help.  25 yrs of experience was my "tutorial."  Some thing can only be learned through experience, mistakes, and fixing those mistakes.   Take careful notes, learn how all the different parts work, have backups and a backout plan ready.

---

### Post by dbee on 2020-03-08
I don't have access to the dns records of the original server. I only have an EPP key ...

As long as I don't actually delete any emails I should be OK right ?

---

### Post by TheFu on 2020-03-08
I have no idea what an EPP key is. Sorry.
If you want to keep emails, then you need to back them up, into a compatible location and format. Never trust a hosting provider to have the only copy of important data. NEVER.

---

