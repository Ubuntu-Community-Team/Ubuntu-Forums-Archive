---
title: "More Java Issues"
date: 2006-06-05
forum: Desktop Environments
---

### Post by totalnoob on 2006-06-05
I'm trying to run limewire.. I installed java and JRE from Easyubuntu then removed and reinstalled limewire. This is what I get then I try to run Limewire
(using dapper)

root@kryoblue-desktop:/home/kryoblue/Desktop# limewire
Starting LimeWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. LimeWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
root@kryoblue-desktop:/home/kryoblue/Desktop# apt-get install sun-java5-jre

please help! Thanks

---

### Post by magnusbb on 2006-06-05
You will have to use this command to make sure the Sun's Java is default on your system:

sudo update-alternatives --config java

And be sure to select the one you recently installed.

---

