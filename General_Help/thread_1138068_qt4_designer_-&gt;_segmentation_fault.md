---
title: "qt4 designer -&gt; segmentation fault"
date: 2009-04-26
forum: General Help
---

### Post by Diaboflo on 2009-04-26
Hi,
I have problems with the qt4 designer. I can't start the program it always throws a segmentation fault in the very beginning. Not even the splash screen starts up. I tried reinstalling it but that didn't solve the problem.
I have no idea how to start looking for the cause of this problem...
Can anyone give me a hint what to do?
Thanks,
Flo

---

### Post by conscious on 2009-04-26
First, run designer-qt4 in terminal. It will possibly give you some error messages before dying. You can use this information to identify the problem.

You may also file a crash report. To do this, enable apport with ```
sudo force_start=1 /etc/init.d/apport start
``` and run the crashing program. Apport will assist you in filing a bug.

---

### Post by Diaboflo on 2009-04-29
Thanks, I submitted the bug. I guess that might take a while given the number of reported bugs on that website...
Is there any other thing I could possibly do? designer-qt4 worked well before I updated it recently.
Cheers,
Flo

---

