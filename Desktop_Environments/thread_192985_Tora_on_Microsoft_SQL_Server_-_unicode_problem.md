---
title: "Tora on Microsoft SQL Server - unicode problem?"
date: 2006-06-09
forum: Desktop Environments
---

### Post by Nobber on 2006-06-09
I'm using tora 1.3.18 on Kubuntu 6.06 against a Microsoft SQL Server database (running on a VMware VM) using ODBC. Now, you might already think that I'm asking for trouble, but bear with me! 
 
I can connect and run queries just fine, but the output from some text columns (e.g. 'name' in the sysusers table) appears garbled. Specifically, unprintable characters show up between what should be consecutive characters. For example: 
 
d?b?_?a?c?c?e?s?s?a?d?m?i?n? 
 
Is this a unicode issue? If so - or even if not - does anyone have any idea how I can fix it?

---

### Post by Nobber on 2006-06-16
No one got any idea about this? It's frustrating - I can use **knoda** and **Base** (the OpenOffice.org database front-end) to connect to the SQL Server database without problems, but those two applications are not as capable or admin-friendly as **tora**. :(

---

### Post by lamego on 2006-06-16
You can create an add an user and set it with a non unicode locale to see if it is really related to the unicode support.

---

### Post by Nobber on 2006-06-16
Well I've tried doing

```
LANG=en_GB tora
```

but that doesn't make any difference. Is that equivalent to what you're suggesting?

---

