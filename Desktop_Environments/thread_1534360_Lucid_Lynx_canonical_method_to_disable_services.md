---
title: "Lucid Lynx: canonical method to disable services?"
date: 2010-07-19
forum: Desktop Environments
---

### Post by jbatista on 2010-07-19
Hi everyone,

Until *Karmic Koala* I could enable/disable services at startup (such as *ssh* or *mysql*) by issuing a **update-rc.d -f *someservice* remove**. On reboot, it would no longer run, and I could re-enable if necessary by, for example, running a **update-rc.d *someservice* default**.

However, it seems that now in *Lucid Lynx* this no longer works. For example, if I do a **nmap localhost** I can see that the ports for the respective services are open, therefore I assume they are likely running (which an attempted access confirms).
For example, if I do a **/etc/init.d/ssh stop**, the ssh service is respawned. I've found that **service ssh stop** or **initctl stop ssh** effectively stops the service (i.e. it is no longer "respawned" if "killed"). But so far I haven't found documentation that conclusively indicates how to disable the service start on (re)boot.

So I ask you, what is now the currently "canonical" or "standard" way to enable/disable these services (particularly ones such as ssh or mysql) from starting on boot on Ubuntu? 
I'd like to avoid having to remove the respective packages if possible (as some posts suggest), since in some occasions I'm interested in manually running those services -- therefore, having to install/uninstall packages is impractical.

Thank you in advance.

---

### Post by jbatista on 2010-07-21
To answer my own question, here goes:

Refer to: [http://www.linuxplanet.com/linuxplanet/tutorials/7033/1/](http://www.linuxplanet.com/linuxplanet/tutorials/7033/1/)
Here, the author describes that starting from Lucid Lynx the **Upstart startup manager** controls some services, instead of the good-and-old SysV. Therefore, this requires editing (and commenting) the **start** and **stop** lines in the respective files under directory **/etc/init** (not to be confused with /etc/init.d).

---

