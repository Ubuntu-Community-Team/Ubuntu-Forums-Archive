---
title: "disable smbd daemon"
date: 2005-08-23
forum: Desktop Environments
---

### Post by bfarris on 2005-08-23
The administrator for the network I want to plug my laptop into on campus has demanded that I not run samba for security reasons.  I already know how to stop using "/etc/init.d/samba stop".  My problem is that smbd daemon is run at boot time and I would like to disable this so that it is only turned on manually.  Does anyone know how to do this?  

thanks

---

### Post by heimo on 2005-08-23
Enable universe:
[https://wiki.ubuntu.com/UniversePackages]("https://wiki.ubuntu.com/UniversePackages")

Install package rcconf (through synaptic OR terminal):
 ```
sudo apt-get install rcconf
``` 

Run sudo rcconf, uncheck samba.

What this will do is change
/etc/rc2.d/[color=Red]S[/color]20samba
symlinks name into this:
/etc/rc2.d/[color=Red]K[/color]20samba
and it won't start during boot anymore.

So, there's quicker, alternative way to do it:
 ```
sudo mv  /etc/rc2.d/S20samba  /etc/rc2.d/K20samba
```

---

### Post by bfarris on 2005-08-23
Thank you very much, that seems to have worked great.

---

