---
title: "Terminal Error"
date: 2009-01-30
forum: General Help
---

### Post by purpleshock on 2009-01-30
Hello there,
I've been trying to install the JRE using instructions that can be viewed at [http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html]("http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html")

I type the command: sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

from here it will promt me for my password and then give me the error message:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

how should i fix/get around this?

Thanks!

---

### Post by Slim Odds on 2009-01-30
> **purpleshock said:**
> Hello there,
I've been trying to install the JRE using instructions that can be viewed at [http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html)

I type the command: sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

from here it will promt me for my password and then give me the error message:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

how should i fix/get around this?

Thanks!

Duh:```
sudo dpkg --configure -a
```

---

### Post by oldos2er on 2009-01-30
If you're stuck at the ncurses screen where the EULA is, use Tab to highlight 'ok' then press Enter.

---

