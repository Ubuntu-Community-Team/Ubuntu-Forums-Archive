---
title: "Task manager for ubuntu"
date: 2009-04-24
forum: General Help
---

### Post by santhoshgr on 2009-04-24
:(sometimes , the apps in ubuntu get stuck and i dont have any chance except to restart...
is there any task manager kinda thing in ubuntu to kill processes as we have in windows?

pls anyone help....

---

### Post by gettinoriginal on 2009-04-24
System > Admin > System Monitor > Processes > highlight process then lower right, "end process". :P  Welcome to Ubuntu

---

### Post by plucky on 2009-04-24
**System > Administration > System Monitor** and select  "Processes" Tab.

Right click on the process you want to stop and select kill.


Or 

Right Click on the panel and select "Add to Panel" and add the "Force Quit" icon.

Good Luck

---

### Post by jamessnell on 2009-04-24
At the command line you can also run:```
top
```

If you see a process that needs killing type "k", then enter the pid and press enter. If you provide the -9 flag, it'll kill the process in a ruthless forceful way, where as the default kill signal may not succeed as it nicely tells the process to go off itself.

---

