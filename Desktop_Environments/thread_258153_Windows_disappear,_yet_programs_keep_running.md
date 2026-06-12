---
title: "Windows disappear, yet programs keep running"
date: 2006-09-15
forum: Desktop Environments
---

### Post by noeffred on 2006-09-15
I've got a problem lately after switching back from Xgl to plain X. From time to time without a proper trigger, all windows disappear yet the programs themselves keep running (ps -A lists all the running beautifully).
The programs do not crash, as there should be some sort of info on that in my .xsession-errors file.

Restarting Metacity doesn't help. I have to killall the programs and restart them one by one, losing unsaved data (really p***** me off)...](*,) 

Possibly there are some problematic packages still installed from the Xgl stuff. How would I restore all packages to the original Ubuntu ones?

Anyone had this problem before and knows an easy fix (or an hard fix for what I care)?

---

### Post by gborzi on 2006-09-15
If you remove or comment the xgl repositories in your /etc/apt/sources.list and press the reload button in Synaptic, the packages you have installed for xgl will be shown (pressing the Status button) as "Installed (local or obsolete)". So you can easily identify and uninstall them (or downgrade to the default packages).

---

