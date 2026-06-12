---
title: "EOF error"
date: 2010-07-07
forum: Desktop Environments
---

### Post by yastackman on 2010-07-07
ProblemType: Bug
DistroRelease: Ubuntu 10.04LTS
Emulator: GNOME 2.29.6
SHELL=/bin/bash
HOME=/home/fujimon
 When I use 'sed-i' from the commandline , I push ctrl-c on my  keyboard with command  not  enclosed  by  the right double
 quotation mark  `"' ,
 After this , error message described below  appears ;
 fujimon@fujimon-desktop:~$ sed -i "1 i \
 > ^C
fujimon@fujimon-desktop:~$ sed -i "1 i \
 > bash: unexpected EOF while looking for matching `"'
bash: syntax error: unexpected end of file
 I am not able to edit new text document file made in  home directory  and deeper directory  using 'sed -i' from commandline.
 But,I can edit new text document file using gedit.
 Please help me.

---

