---
title: "No local login?"
date: 2009-02-27
forum: General Help
---

### Post by Desrik on 2009-02-27
Ubuntu 8.04 Hardy Heron only boots to GDM remote login screen. Can't login localy. Any ideas on how to fix it?

---

### Post by Guidoo on 2009-02-27
Try running ```
sudo gdmsetup
``` from a terminal and check the settings there!

---

### Post by Desrik on 2009-02-27
tried that already all the settings seem ok...I even tried disabling remote login and still get the same thing. I have to type localhost into the box and click add in order to log on. then I dont get network

---

### Post by brendanrdalegend on 2009-03-17
i have the same problem but when i tried gdmsetup it seemed to be the settings for the live cd i was using

---

### Post by brendanrdalegend on 2009-03-17
had the same problem just fixed it by removing the gdm.config-custom file in
/ect/gdm/

---

