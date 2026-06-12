---
title: "Nvidia 195.36.24 driver, Ubuntu 10.04 lucid, memory leak"
date: 2010-05-21
forum: Desktop Environments
---

### Post by hihihi100 on 2010-05-21
Hi there:

I dont know if this issue has already been solved, or if there are other threads dealing with it, but Im quite desperate with this bug that has been annoying me since I upgraded from 9.10 to 10.04.

Firs I thought it would be GEM related, but Im using a proprietary graphics card, so thats not the way to solve it.

I experience the problems a memory leak provokes, mainly that, as time goes by with the laptop turned on, the system needs more resources to execute simple actions, and it freezes too many times. Plus IBUS will, suddenly, stop working (I still don't know if it is related or not), and, most of the times I log in, Notification Area 2.30.0 will load with errors.

Please tell me what command do I have to paste in a terminal to know more about this issue, Ill be answering any question you may have...

And, if this issue has already been solved, please, kindly paste the URL to the solved thread

---

### Post by epi 1:10,000 on 2010-05-24
I have the same problem w/ my ATI 4850 an the fglrx 10.4 driver.  I f i run the "free -m -s 15" in the terminal to mesure the free memory ever 15 seconds I find that I keep losing free memory the longer the system has been up.

---

### Post by Asraniel on 2010-07-04
same here, had to change to nouveau.

---

### Post by schnelle on 2010-07-04
For ati fglrx driver, run ```
glxinfo
``` in terminal and leaked memory will be fixed. But you have to run this command from time to time.

---

