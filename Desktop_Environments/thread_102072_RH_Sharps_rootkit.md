---
title: "RH Sharps rootkit"
date: 2005-12-11
forum: Desktop Environments
---

### Post by CharlieC on 2005-12-11
I ran rkhunter and got this message:
Rootkit 'RH-Sharpe's rootkit'...                           [ Warning! ]

             --------------------------------------------------------------------------------
             Found parts of this rootkit/trojan by checking the default files and directories
             Please inspect the available files, by running this check with the parameter
             --createlogfile and check the log file (current file: /var/log/rkhunter.log).

Here is the log:
Start scan RH-Sharpe's rootkit ***
[09:08:02]   - File /bin/lps... OK. Not found.
[09:08:02]   - File /usr/bin/lpstree... OK. Not found.
[09:08:02]   - File /usr/bin/ltop... OK. Not found.
[09:08:02]   - File /usr/bin/lkillall... OK. Not found.
[09:08:02]   - File /usr/bin/ldu... OK. Not found.
[09:08:02]   - File /usr/bin/lnetstat... OK. Not found.
[09:08:02]   - File /usr/bin/wp... OK. Not found.
[09:08:02]   - File /usr/bin/shad... OK. Not found.
[09:08:02]   - File /usr/bin/vadim... OK. Not found.
[09:08:02]   - File /usr/bin/slice... WARNING! Exists.
[09:08:02]   - File /usr/bin/cleaner... OK. Not found.

I googled and found precisely one mention of /usr/bin/slice giving a false positive. 

Does anyone have any knowledge of this?

Do I have to wipe out my system now?

Charlie

---

