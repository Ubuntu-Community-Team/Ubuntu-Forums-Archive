---
title: "Issues with EVE install"
date: 2009-02-06
forum: General Help
---

### Post by echo314 on 2009-02-06
Is there a fix the this issue? I have seen several other topics, but none have fixed this. 

```
echo@echo-desktop:~$ eve
Single-user install...
This is the update checker... 
Running /home/echo/.cedega/.updater/cedega_updater.py
/home/echo/.cedega/.updater/gddb.py:26: RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
  import gddb_parser
Running... /home/echo/.cedega/.ui/runGUI
/home/echo/.cedega/.ui/gddb.py:24: RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
  import gddb_parser
echo@echo-desktop:~$ X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12

```

---

### Post by ChimpofDOOM on 2009-02-06
From what I remember back in my eve playing days.

Install Wine, download the windows client and off you go!

Works better than the Cedega client, it's filled with bugs.

---

### Post by echo314 on 2009-02-06
So Wine + the Windows client works better then the official Deb package with Cedega built in? 

I'm not doubting you, but there seems something odd with this picture...I'll give it a try, thanks!

---

