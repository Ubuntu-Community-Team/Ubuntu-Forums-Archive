---
title: "can't find gkrellm GUI after loading software on Hardy"
date: 2009-02-13
forum: General Help
---

### Post by ozguitarplayer on 2009-02-13
Hi, 
I have loaded lm -sensors and gkrellm yet I cannot find the GUI. It was easy to find on Intrepid Ibex but using Hardy Heron I look and look and can't find the GUI.....any suggestions?

---

### Post by drs305 on 2009-02-13
If it's not in System Tools > Gkrellm you can make a launcher: Right click on the panel, Add to Panel, Custom Application Launcher. Command: /usr/bin/gkrellm 

You can find the run command of an app with:
```
which <appname>   # example:  which gimp
```

You can find app file locations with:
```
whereis <appname>  # example: whereis gimp
```

The user config files are in ~/.gkrellm2

---

### Post by ozguitarplayer on 2009-02-13
Perfect...thanks heaps drs305

---

### Post by dcstar on 2009-02-14
> **ozguitarplayer said:**
> Hi, 
I have loaded lm -sensors and gkrellm yet I cannot find the GUI. It was easy to find on Intrepid Ibex but using Hardy Heron I look and look and can't find the GUI.....any suggestions?

It looks like the 8.04 version of the gkrellm package does not install the menu item correctly - it was also missing from my menus.

---

