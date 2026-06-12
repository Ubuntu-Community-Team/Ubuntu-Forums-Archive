---
title: "SNMPD startup error | undefined symbol"
date: 2009-05-04
forum: General Help
---

### Post by john_d13 on 2009-05-04
For the life of me i cant figure out this issue why snmpd wont restart.  im getting this error:

service snmpd restart
 * Restarting network management services:                                                                   /usr/sbin/snmpd: symbol lookup error: /usr/sbin/snmpd: undefined symbol: smux_listen_sd

I purged, removed and reinstalled and same problem.

* Starting network management services:                                                                     /usr/sbin/snmpd: symbol lookup error: /usr/sbin/snmpd: undefined symbol: smux_listen_sd
invoke-rc.d: initscript snmpd, action "start" failed.
dpkg: error processing snmpd (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 snmpd
E: Sub-process /usr/bin/dpkg returned an error code (1)


please someone help

---

### Post by pastalavista on 2009-05-04
Open Synaptic  Package Manager and look for broken packages or missing dependencies.

---

### Post by john_d13 on 2009-05-04
Do i just click on properties of snmpd in the package manager ?

Will it tell me if there are broken packages ?

All the Depends are installed and there are 2 conflicts which are snmp package.  I cant even install or uninstall the snmp package I get the same error

---

### Post by pastalavista on 2009-05-04
The Synaptic GUI is kinda convoluted. Try this ```
sudo aptitude --safe-resolver
```

---

### Post by john_d13 on 2009-05-05
thanks for the reply.  Im new to this tool, would you be kind enouph to guide me through.

I attached a screener.

---

### Post by john_d13 on 2009-05-07
anyone ?

---

### Post by pastalavista on 2009-05-07
Sorry I didn't get back to you. I'm not completely proficient with full-resolver either. I do know you use the arrow keys to navigate and enter to select. Find the package that's giving you trouble and use the menu commands (g,u,? etc) to perform actions on the selected packages.

I got all my info by using the terminal command ```
man aptitude
```

Synaptic Package Manager does the same thing and probably isn't any more difficult than full-resolver except resolver makes finding the unresolved packages easier.

---

