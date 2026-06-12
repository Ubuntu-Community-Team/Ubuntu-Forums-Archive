---
title: "How do I replace lines in the configuration sripts"
date: 2005-12-13
forum: General Help
---

### Post by PryGuy on 2005-12-13
Peace, mates! ;)
 
I have a quesion here:
I've made up a script that automatically installs additional packages that I need after the Ubuntu installation (nvidia-glx for instance). And the question is, is it possible to replace lines in say /etc/X11/xorg.conf with the lines that I need? For instance I have a 15" display on my Ubuntu box and by default the system starts in 1280X1024 after the installation. I'd like to edit the "Modes" sections using the script to make the 1024X768 resolution the first in the lists.

Thank you in advance!:D 

P.S. :idea: I think it'd be great if the forum admins added a sub-forum here called "Ubuntu unattended"

---

### Post by RAOF on 2005-12-13
Ah, some bash-script-fu.  I'm not familiar with it myself, but I believe that sed is the command you're after.

---

### Post by 23meg on 2005-12-13
sed is the stream editor; probably ed will be more suitable. ```
man ed
```will give you the details. Also check out perl and awk if you can't get what you want done.

---

