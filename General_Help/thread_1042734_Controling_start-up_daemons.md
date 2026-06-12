---
title: "Controling start-up daemons"
date: 2009-01-17
forum: General Help
---

### Post by theQmaster on 2009-01-17
How do I control the daemons that start up ?
It happened to have 3 version of postgresql starting.

Is that driven by /etc/rcX.d/ folder content and the symbolic links within those folders ?

Thanks!
Q

---

### Post by x33a on 2009-01-18
you can go to system -> administration -> services and disable them from there.

---

### Post by ibutho on 2009-01-18
You can use the tool described above as well as update-rc.d which is a command line tool.

---

