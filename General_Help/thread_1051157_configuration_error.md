---
title: "configuration error"
date: 2009-01-26
forum: General Help
---

### Post by alexisd on 2009-01-26
GConf error: No database available to save your configuration: Unable to store a value at key '/apps/nautilus/preferences/navigation_window_saved_maximized', as the configuration server has no writable databases. There are some common causes of this problem: 1) your configuration path file /etc/gconf/2/path doesn't contain any databases or wasn't found 2) somehow we mistakenly created two gconfd processes 3) your operating system is misconfigured so NFS file locking doesn't work in your home directory or 4) your NFS client machine crashed and didn't properly notify the server on reboot that file locks should be dropped. If you have two gconfd processes (or had two at the time the second was launched), logging out, killing all copies of gconfd, and logging back in may help. If you have stale locks, remove ~/.gconf*/*lock. Perhaps the problem is that you attempted to use GConf from two machines at once, and ORBit still has its default configuration that prevents remote CORBA connections - put "ORBIIOPIPv4=1" in /etc/orbitrc. As always, check the user.* syslog for details on problems gconfd encountered. There can only be one gconfd per home directory, and it must own a




im getting that long error message 
please help me im new to ubuntu

---

### Post by cariboo on 2009-01-26
Please use the [noparse]```

```[/noparse] tags around the output of an error message, to make it easier to read.

I think from the error you are getting it is saying you have 2 ~/.gconf directories. To check this out, open Nautilus (Paces-->Home folder) and press Alt-h, this will show all the hidden files and directories, if you see 2 .gconf directories delete one.

Jim

---

