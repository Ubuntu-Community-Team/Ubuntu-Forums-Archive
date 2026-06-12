---
title: "HP 4480 will not print from v10.04"
date: 2010-09-06
forum: Desktop Environments
---

### Post by cboyle739 on 2010-09-06
I have just purchased a new HP 4480 printer, on version 10.04 LTS. Made all the connections, the OS recognizes the printer as HP 4400 series, all looks good. When I run a test page, it runs through the process, I see the job in the print queue and even see the communication light on the printer blinking. After 5 seconds or so I receive a message that says the print job has stopped.

Has anyone run into this issue before, and did I miss a step in setting up the printer?

Thanks, 
Chris

---

### Post by ajgreeny on 2010-09-06
If this is an all-in-one deskjet f4480, it should work in all ubuntu versions from 8.04 on, so something must have gone wrong in your setup, I think.

Delete that printer from **System ->Administration ->Printing** and try installing again, though normally the system finds it and tells you it's ready for use without you doing anything at all.

make sure you have hplip installed on your system, though it is usually installed as default, and also get the hplip-gui which gives you the HP Toolbox, a great little tool for managing the printer/scanner.

---

### Post by cboyle739 on 2010-09-06
ajgreeny,

Thanks for the tip, solved my problem, greatly appreciated

---

