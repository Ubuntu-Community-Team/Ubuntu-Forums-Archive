---
title: "Graphical login absent while running script command"
date: 2014-07-22
forum: Desktop Environments
---

### Post by clarkgr1 on 2014-07-22
I'm running Ubuntu 12.04 LTS (lightdm manager) and attempting to log all terminal input and output using both[FONT=courier new] auditd[/FONT] and the [FONT=courier new]script[/FONT] command. For users, I place "[FONT=courier new]script -a -f /LOG_files/LOG.txt[/FONT]" in their write-protected [FONT=courier new]~/.profile[/FONT] ([FONT=courier new]auditd[/FONT] also writes to the same file). For some reason, the [FONT=courier new]script[/FONT] command causes graphical login to abort - very similar to authority problems others had with [FONT=courier new]~/.Xauthority[/FONT], but this is not the problem. 

(I've also tried launching the [FONT=courier new]script[/FONT] command at boot via[FONT=courier new] /etc/init.d/[/FONT] which solves the graphical login problem, but then logging doesn't write to the file).

Any ideas would be great!

---

