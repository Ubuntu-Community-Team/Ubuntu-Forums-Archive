---
title: "[SOLVED] Problem with CCSM"
date: 2008-12-26
forum: General Help
---

### Post by Jakey_TheSnake on 2008-12-26
When attempting to run "ccsm" it returns with the error it's not installed. 
It says to install it run "sudo apt-get install compizconfig-settings-manager". 

So I do, and apparently the package does not exist. I checked synaptic and all packages to do with compiz are already installed. I even checked all compiz related packages in the repositories and they ae all installed too. 

Please advise.

---

### Post by LowSky on 2008-12-26
Make sure you have Propritary graphics drivers on and working, 

copy and past this into your terminal and run it
```

sudo apt-get update && sudo apt-get remove compizconfig-settings-manager  && sudo apt-get update && sudo apt-get install compizconfig-settings-manager
```

---

### Post by Jakey_TheSnake on 2008-12-26
Will try code in a minute, I think I haven't got the right repositories enabled, seeing as it also couldn't find the package "msttcorefonts" which I *know* exists. 

Which repositories would I need to have enabled, or what do I need to do to enable them? Something in Software Sources. 

Something blindingly obvious no doubt.

edit: solved, thanks anyway.

---

