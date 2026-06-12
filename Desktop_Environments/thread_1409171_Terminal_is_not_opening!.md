---
title: "Terminal is not opening!"
date: 2010-02-17
forum: Desktop Environments
---

### Post by gansvv on 2010-02-17
Terminal does not open anymore in my Ubuntu machine. Kconsole and Xterm do work though. Its just gnome-terminal that is not opening! 
I get the following error from GConf (below), when starting gnome-terminal from the Kconsole. Can someone please tell me what is happening? 

Thanks in advance.

```

$ gnome-terminal                                                           
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)                                   
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)                                   
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)                                   
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)                                   
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)                                   
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)                                   
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)                                   
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Server ping error: IDL:omg.org/CORBA/COMM_FAILURE:1.0)                                   
**                                                                                   
ERROR:terminal-app.c:1444:terminal_app_init: assertion failed: (app->default_profile_id != NULL)                                                                          
Aborted 

```

---

### Post by gansvv on 2010-02-17
Okay, a restart (apparently removed the lock) and solved the issue. But what was happening there?

I found the same issue mentioned here:
[http://bbs.archlinux.org/viewtopic.php?id=56472](http://bbs.archlinux.org/viewtopic.php?id=56472)

---

