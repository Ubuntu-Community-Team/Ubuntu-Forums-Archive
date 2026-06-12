---
title: "Help i screwed something up bad :("
date: 2006-03-12
forum: Desktop Environments
---

### Post by nismoskys on 2006-03-12
i was trying to get rid of too many programs that were opening up at startup so i went to System -> Preferences -> Sessions and went to Current Session and my dumba$$ deleted all the things there that had an Order of 50(there were some with an order of 40 and 20). Now i get a LOT of errors when i start X including

Nautilus can't be used now, due to an unexpected error from Bonobo when attempting to register the file manager view server.

, i cant get to the Gnome Login screen.. Logging out just takes me to the big black command line (lol i dont know what its called). Luckily after clicking OK on like 20 errors, i eventually get my regular stuff and everything SEEMS to be working fine after that.

how can i fix thiS??? please.
and thank you.

---

### Post by nismoskys on 2006-03-12
i googled around a bit and i THINK that if i

apt-get upgrade gnome-utils control-themes gnome-themes

that it will fix it?

any input would be appreciated.
(currently apt-get upgrad**ing** gnome-utils)

---

### Post by fimbulvetr on 2006-03-12
Well if you just killed things that were running, and didn't change anything affecting start up processes, I'd say that rebooting should fix everything. 

The reason restarting X doesn't work is because X starts processes and those started processes start other processes. X sees them running and doesn't start them, so they don't get a chance to start their processes.

---

### Post by nismoskys on 2006-03-12
hmm.. seems good lemme go reboot thanks :)

---

### Post by nismoskys on 2006-03-12
sweeet worked perfectly, thanks alot man.

---

