---
title: "how to run a script at the login screen"
date: 2009-06-13
forum: General Help
---

### Post by alphageek89 on 2009-06-13
I added a python script to the startup application list .I want it to start at the login screen,Is that possible?

---

### Post by briguy47 on 2009-06-14
> **alphageek89 said:**
> I added a python script to the startup application list .I want it to start at the login screen,Is that possible?


Here are the instruction to run a script at boot before GDM kicks in.  :D

1. Write your a shell script pointing to your python script:

```
#!/bin/sh
python path/to/pythonscript.py
```2. Copy the shell script  into **/etc/init.d/**.

```
sudo cp yourscript /etc/init.d/
```3.  Change the file permissions with:

```
sudo chmod +x /etc/init.d/yourscript
```4. Update rc.d with:

```
sudo update-rc.d /etc/init.d/yourscript defaults
```5. Reboot and that should do it.

Hope that helps.  Let me know if you have any trouble. :D

---

