---
title: "How can I force firefox to crash on me?"
date: 2009-05-01
forum: General Help
---

### Post by degel3030 on 2009-05-01
I am looking for a way (or bug) that will allow me to get firefox to crash. If you are wondering why? I am testing and need to emulate a crash so I can see how other clients react
Thanks for any help/guidence
oh and if it's a site that will always crash for firefox, it must be safe for work

Firefox
Ubuntu LTS 8.04.2

Thanks for any help

---

### Post by cybergalvez on 2009-05-01
why not just kill it with kill -9 <firefoxpid> or killall firefox

---

### Post by lensman3 on 2009-05-01
Or "kill-3 pid".  If you set the "ulimit -c <coresize>" command in your bash script the -3 will cause a core dump.  Then you can use gdb to debug the executable.

---

### Post by degel3030 on 2009-05-12
Thanks, not exactly what I was looking for, I wanted to test how crashing one instance of firefox would effect other people that are logged in

---

