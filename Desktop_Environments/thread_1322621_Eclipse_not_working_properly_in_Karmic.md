---
title: "Eclipse not working properly in Karmic"
date: 2009-11-11
forum: Desktop Environments
---

### Post by eugen_nicoara on 2009-11-11
I'm having a very strange issue with Eclipse IDE. 

I had Ubuntu 9.04 then I upgraded to 9.10. Then I wrecked the system and I had to reinstall it without formatting the disk. Since then it seems like the buttons are not working in modal windows in Eclipse. 

For example, if I try to change the build path for a project all I can do is to open the properties window for that project. When I select a jar file and push the Edit button to change it nothing happens.

I tried with both Eclipse IDE for Java EE Developers and Eclipse IDE for Java Developers but the result was exactly the same. I did not have this problem when I was using 9.04 or after the upgrade to 9.10. It seems like it has something to do with the last installation.

Any ideas what might be the problem?

Thanks!

---

### Post by kellemes on 2009-11-11
Did you get Eclipse from the repositories?
If so.. that never worked for me, better get it from the [Eclipse site]("http://www.eclipse.org/downloads/").

Not sure if this is related..
I had this issue with Eclipse the mouse wouldn't work when pushing a button but using the keyboard it worked fine.
So, <tab> to the button and <enter> to push.

---

### Post by yanns on 2009-11-11
Add "export GDK_NATIVE_WINDOWS=true" before starting eclipse.
This problem will be fixed in Eclispe 3.6 normally.

---

### Post by eugen_nicoara on 2009-11-11
> **yanns said:**
> Add "export GDK_NATIVE_WINDOWS=true" before starting eclipse.


That solved the problem. Thank you!

---

### Post by nasif_20 on 2009-11-29
it's solved my problem also

---

### Post by nasif_20 on 2009-11-29
edit eclipse.ini with       export GDK_NATIVE_WINDOWS=true

---

