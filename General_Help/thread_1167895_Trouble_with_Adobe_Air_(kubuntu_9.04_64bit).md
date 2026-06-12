---
title: "Trouble with Adobe Air (kubuntu 9.04 64bit)"
date: 2009-05-23
forum: General Help
---

### Post by Wired84 on 2009-05-23
Trying to use a few apps that use adobe air, however I am having a lot of issues installing them.

I have been able to install adobe air from command line, but did take a bit of messing about with. 
However when I try to install an air app the air icon flashes and the cursor spins, but then nothing happens. I have tried reinstalling air, but have had no such luck installing any air apps.

Any ideas? Could there be anything stopping this from working?

---

### Post by Wired84 on 2009-05-23
No probs i gpt the error

'Error loading the runtime (libadobecertstore.so: cannot open shared object file: No such file or directory)'

fixed it with the command;

'sudo cp /usr/lib/libadobecertstore.so /usr/lib32'

more info here [http://kb2.adobe.com/cps/408/kb408084.html](http://kb2.adobe.com/cps/408/kb408084.html)

---

