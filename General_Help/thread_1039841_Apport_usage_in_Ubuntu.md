---
title: "Apport usage in Ubuntu"
date: 2009-01-14
forum: General Help
---

### Post by starcraft2fan on 2009-01-14
I enabled apport by activating the setting in /etc/default/apport, rebooted, then set |ulimit -c 1000| in the console. I am running a console shell binary program that crashes occasionally but which I'm trying to trace. So far the method I listed generates a core dump that I can use gdb to analyze.

However, what I couldn't figure out was why there wasn't a listing in /var/crash, in fact there was nothing present there. I checked other python or GUI programs to force them to crash and they did crash and produce the apport report in /var/crash, but not for the console shell binary program, compiled debug and with symbols.

---

