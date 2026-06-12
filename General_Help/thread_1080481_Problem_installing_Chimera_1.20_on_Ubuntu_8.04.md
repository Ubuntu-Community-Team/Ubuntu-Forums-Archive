---
title: "Problem installing Chimera 1.20 on Ubuntu 8.04"
date: 2009-02-25
forum: General Help
---

### Post by sanquinia on 2009-02-25
Pentium Core 2 Q6600
4Gb RAM, 160Gb HDD
Ubuntu 8.04. desktop

Chimera appears to install when i install is as directed in the install guide given with the install files.

'Chimera uses auto-conf tool, therefore compilation should be straightforward. Change directory to the chimera and run the following commands to compile the code:

./configure --prefix='current directory'
make install'

When i type the command 'chimera' to start the program the command is not found.

Help !?!

Thanks

sanquinia

---

 /bin/bash ../libtool  --mode=install /usr/bin/install -c  dhttest /usr/local/bin/dhttest
/usr/bin/install -c dhttest /usr/local/bin/dhttest
 /bin/bash ../libtool  --mode=install /usr/bin/install -c  dht /usr/local/bin/dht
/usr/bin/install -c dht /usr/local/bin/dht
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/user/Desktop/chimera/test'
make[1]: Leaving directory `/home/user/Desktop/chimera/test'
make[1]: Entering directory `/home/user/Desktop/chimera'
make[2]: Entering directory `/home/user/Desktop/chimera'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/user/Desktop/chimera'
make[1]: Leaving directory `/home/user/Desktop/chimera'
 user@user-desktop6:523  ~/Desktop/chimera>chimera
bash: chimera: command not found

---

### Post by geraldm on 2009-02-25
You would need to type "./chimera" to execute it.
The leading ./ tells the shell to look in the current directory.

Gerald

---

