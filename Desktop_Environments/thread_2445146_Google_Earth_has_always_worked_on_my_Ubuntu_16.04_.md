---
title: "Google Earth has always worked on my Ubuntu 16.04 but now won't launch"
date: 2020-06-09
forum: Desktop Environments
---

### Post by ShowMeGrrl on 2020-06-09
Hi -- I'm running Ubuntu 16.04 (64-bit) on a

System76 Wild Dog desktop computer with
64GB memory
Intel Core i7-6700 CPU @ 3.40 GHz x 8
GeForce GTX 750 Ti/PCle/SSE2

Google Earth has always run fine on this computer, but now the program won't launch. 

Anybody know why I am having this problem and what I can do to fix it?

Thanks!

---

### Post by monkeybrain20122 on 2020-06-11
Since you don't provide any error message (you will see them if try to launch GE on the terminal) I can only guess. Open the file manager, show hidden files and look for the folder .googleearth (the "." in front means it is a hidden file) Open it and then delete the file inside called instance-running-lock.

---

### Post by ShowMeGrrl on 2020-06-11
Thanks monkeybrain 20122. You suggestions worked perfectly. I tried to launch google-earth in the terminal window and got error message that the program was already running. I rebooted my computer and got the same message again. I then deleted the "instance-running-lock" folder inside the hidden .googleearth folder, as instructed both by you and the terminal window, and now Google Earth is launching as it should. Thanks for the help!

---

