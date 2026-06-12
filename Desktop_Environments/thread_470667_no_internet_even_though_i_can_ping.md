---
title: "no internet even though i can ping"
date: 2007-06-11
forum: Desktop Environments
---

### Post by fouadk on 2007-06-11
hey all

i have installed 7.04 and i have the internet problem...my ubuntu pc in connected to a windows pc that is sharing an internet connection through ICS....all ips are set correctly and i can ping the windows pc by ip but not by hostname....

what is the solution....

btw i didnt have this problem in any of 5.10 6.06 6.10....its the first time i encounter such thing

thanks in advance

---

### Post by pestilence on 2007-06-11
If you are trying to ping by hostname then you either need full DNS support or edit your /etc/hosts file and add the windows PC there.
Is the hostname an official DNS record? or an internal name?

---

