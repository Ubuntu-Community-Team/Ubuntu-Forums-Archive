---
title: "Startup option to skip time sync?"
date: 2004-10-17
forum: General Help
---

### Post by tmccartney on 2004-10-17
Hi:

I'm struggling to get my network card working under Ubuntu, and every time I boot my laptop hangs for 30 or so seconds on
"Synchronizing clock to ntp.ubuntulinux.org" - I finally get an error message.

Is there a param I can put in the startup to skip this step for the time being, until I get the wireless card working?

Thanks,

Tracey

---

### Post by triad169 on 2004-10-18
Use the cammond : update-rc.d

To install and remove System-V style init script links.  So to remove the NTP server just do this in a terminal:

```
sudo update-rc.d -f ntpdate remove

```

this will remove ntpdate from the rcS directory and thus remove from startup. 

To add back later just do:

 ```
 sudo update-rc.d ntpdate start 51 S .
```

This will put back a sym link.  

For more info on usage of update-rc.d read

man update-rc.d

[http://www.wlug.org.nz/update-rc.d](http://www.wlug.org.nz/update-rc.d)

[http://www.justlinux.com/nhf/Distribution_Specific/Debian_GNULinux/Debian__Startup_Commands.html](http://www.justlinux.com/nhf/Distribution_Specific/Debian_GNULinux/Debian__Startup_Commands.html)

[http://newbiedoc.sourceforge.net/system/runlevels-intro.html#SCRIPTSTARTSTOP](http://newbiedoc.sourceforge.net/system/runlevels-intro.html#SCRIPTSTARTSTOP)

Triad

---

### Post by tmccartney on 2004-10-18
Thanks!



Tracey

---

