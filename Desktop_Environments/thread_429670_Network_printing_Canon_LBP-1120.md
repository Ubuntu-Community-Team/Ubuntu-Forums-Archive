---
title: "Network printing: Canon LBP-1120"
date: 2007-05-01
forum: Desktop Environments
---

### Post by baadkarma on 2007-05-01
I have an Canon LBP-1120 laser printer connected to a XP computer. But i cant get it to work.

SMB networking works fine, im running the LBP-810 driver (who is supposed to work with this printer). 

I can choose both the computer and the printer in installation in ubuntu (its discovered by installer)

It says "Ready" in printspooler window

This might be a issue with authorization (my guess), ive made a user named "jojje" on XP computer but still cant get it to work.

when using "print test page" it sends page to printer and it then shows "job-stopped". 

Please help me with this problem!,  ill be happy to provide more info if needed.

//jojje aka baadkarma

---

### Post by baadkarma on 2007-05-03
Problem solved ! :)

For everyone who had this problem i write a mini-howto :).

Download official driver from Canon homepage.
Install it with alien.
extract driverpackage to, and copy the lbp1120.ppd file to your home directory.

Add network printer as usuall and open the newly moved lbp1120.ppd file. 
Works just fine! :).

Forget about the LBP-810 driver i couldnt get that working.

Happy regards Jojje

---

