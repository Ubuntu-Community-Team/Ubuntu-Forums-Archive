---
title: "Kernel update and hanging."
date: 2005-12-21
forum: Desktop Environments
---

### Post by awakatanka on 2005-12-21
When ever there is a new kernel update our i try to install a new kernel adept hangs. 1st i thought well maybe it takes a bit longer to configure but after 1 night i broke it.

I have to do a sudo dpkg --configure -a to solve it then, else i can't access adept in the right way anymore.

Also if i use ktorrent sometimes my cpu use goes up to 100% and doen't work anymore. Pictogram at system tray diseapers also regular and i know that cpu will go up then.

Anyone got a idea/solution, our do i need to report a bug ( if itsn't done already )?

Kubuntu breezy 5.10 with kde 3.5 installed.

---

### Post by tkjacobsen on 2005-12-21
Have you installed the correct kernel for your current arch. That solved a lot of instability problems for me. Just use apt-get in terminal to install linux-i686, linux-k7 etc. 

If adept is still hanging, try synaptic instead.

---

### Post by tseliot on 2005-12-21
Open Konsole and type
```
sudo apt-get install synaptic
```

and you will get synaptic

---

