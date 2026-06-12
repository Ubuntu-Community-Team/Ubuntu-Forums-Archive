---
title: "Serious problem system crash"
date: 2009-05-09
forum: General Help
---

### Post by colau on 2009-05-09
Hi,
I was downloading php5-mysql from synaptic.
Unfortunately electricity is gone.
Now i got a message from top right icon saying system crash.
I tried to install again from synaptic.
This message is shown now.
```

E: dbconfig-common: subprocess post-installation script returned error exit status 2
E: libgd2-xpm: subprocess post-installation script returned error exit status 2
E: libmcrypt4: subprocess post-installation script returned error exit status 2
E: libt1-5: subprocess post-installation script returned error exit status 2
E: php5-gd: dependency problems - leaving unconfigured
E: php5-mcrypt: dependency problems - leaving unconfigured
E: php5-mysql: subprocess post-installation script returned error exit status 2
E: phpmyadmin: dependency problems - leaving unconfigured

```
I also can't install anything from terminal using 
aptitude install <packagename>

---

### Post by colau on 2009-05-09
If i type 
aptitude install gnochm
the result is 
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
The following partially installed packages will be configured:
  dbconfig-common libgd2-xpm libmcrypt4 libt1-5 php5-gd php5-mcrypt 
  php5-mysql phpmyadmin 
0 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up dbconfig-common (1.8.40) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing dbconfig-common (--configure):
 subprocess post-installation script returned error exit status 2
Setting up libgd2-xpm (2.0.36~rc1~dfsg-3ubuntu1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing libgd2-xpm (--configure):
 subprocess post-installation script returned error exit status 2
Setting up libmcrypt4 (2.5.7-5ubuntu1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing libmcrypt4 (--configure):
 subprocess post-installation script returned error exit status 2
Setting up libt1-5 (5.1.2-3) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing libt1-5 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of php5-gd:
 php5-gd depends on libgd2-xpm (>= 2.0.36~rc1~dfsg); however:
  Package libgd2-xpm is not configured yet.
 php5-gd depends on libt1-5 (>= 5.1.0); however:
  Package libt1-5 is not configured yet.
dpkg: error processing php5-gd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php5-mcrypt:
 php5-mcrypt depends on libmcrypt4; however:
  Package libmcrypt4 is not configured yet.
dpkg: error processing php5-mcrypt (--configure):
 dependency problems - leaving unconfigured
Setting up php5-mysql (5.2.6.dfsg.1-3ubuntu4.1) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            No apport report written because MaxReports is reached already
                          dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing php5-mysql (--configure):
 subprocess post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of phpmyadmin:
 phpmyadmin depends on php5-mysql | php5-mysqli; however:
  Package php5-mysql is not configured yet.
  Package php5-mysqli is not installed.
 phpmyadmin depends on php5-mcrypt; however:
  Package php5-mcrypt is not configured yet.
 phpmyadmin depends on dbconfig-common; however:
  Package dbconfig-common is not configured yet.
dpkg: error processing phpmyadmin (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 dbconfig-common
 libgd2-xpm
 libmcrypt4
 libt1-5
 php5-gd
 php5-mcrypt
 php5-mysql
 phpmyadmin
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up libt1-5 (5.1.2-3) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing libt1-5 (--configure):
 subprocess post-installation script returned error exit status 2
Setting up libgd2-xpm (2.0.36~rc1~dfsg-3ubuntu1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing libgd2-xpm (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of php5-gd:
 php5-gd depends on libgd2-xpm (>= 2.0.36~rc1~dfsg); however:
  Package libgd2-xpm is not configured yet.
 php5-gd depends on libt1-5 (>= 5.1.0); however:
  Package libt1-5 is not configured yet.
dpkg: error processing php5-gd (--configure):
 dependency problems - leaving unconfigured
Setting up libmcrypt4 (2.5.7-5ubuntu1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing libmcrypt4 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of php5-mcrypt:
 php5-mcrypt depends on libmcrypt4; however:
  Package libmcrypt4 is not configured yet.
dpkg: error processing php5-mcrypt (--configure):
 dependency problems - leaving unconfigured
Setting up php5-mysql (5.2.6.dfsg.1-3ubuntu4.1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing php5-mysql (--configure):
 subprocess post-installation script returned error exit status 2
Setting up dbconfig-common (1.8.40) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing dbconfig-common (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of phpmyadmin:
 phpmyadmin depends on php5-mysql | php5-mysqli; however:
  Package php5-mysql is not configured yet.
  Package php5-mysqli is not installed.
 phpmyadmin depends on php5-mcrypt; however:
  Package php5-mcrypt is not configured yet.
 phpmyadmin depends on dbconfig-common; however:
  Package dbconfig-common is not configured yet.
dpkg: error processing phpmyadmin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libt1-5
 libgd2-xpm
 php5-gd
 libmcrypt4
 php5-mcrypt
 php5-mysql
 dbconfig-common
 phpmyadmin
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

```

---

### Post by Kareeser on 2009-05-09
Run this:
```
sudo dpkg --configure -a
```

---

### Post by colau on 2009-05-09
> **Kareeser said:**
> Run this:
```
sudo dpkg --configure -a
```
After this "sudo dpkg --configure -a"
The result is
```

Setting up libt1-5 (5.1.2-3) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing libt1-5 (--configure):
 subprocess post-installation script returned error exit status 2
Setting up libgd2-xpm (2.0.36~rc1~dfsg-3ubuntu1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing libgd2-xpm (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of php5-gd:
 php5-gd depends on libgd2-xpm (>= 2.0.36~rc1~dfsg); however:
  Package libgd2-xpm is not configured yet.
 php5-gd depends on libt1-5 (>= 5.1.0); however:
  Package libt1-5 is not configured yet.
dpkg: error processing php5-gd (--configure):
 dependency problems - leaving unconfigured
Setting up libmcrypt4 (2.5.7-5ubuntu1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing libmcrypt4 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of php5-mcrypt:
 php5-mcrypt depends on libmcrypt4; however:
  Package libmcrypt4 is not configured yet.
dpkg: error processing php5-mcrypt (--configure):
 dependency problems - leaving unconfigured
Setting up php5-mysql (5.2.6.dfsg.1-3ubuntu4.1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing php5-mysql (--configure):
 subprocess post-installation script returned error exit status 2
Setting up dbconfig-common (1.8.40) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing dbconfig-common (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of phpmyadmin:
 phpmyadmin depends on php5-mysql | php5-mysqli; however:
  Package php5-mysql is not configured yet.
  Package php5-mysqli is not installed.
 phpmyadmin depends on php5-mcrypt; however:
  Package php5-mcrypt is not configured yet.
 phpmyadmin depends on dbconfig-common; however:
  Package dbconfig-common is not configured yet.
dpkg: error processing phpmyadmin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libt1-5
 libgd2-xpm
 php5-gd
 libmcrypt4
 php5-mcrypt
 php5-mysql
 dbconfig-common
 phpmyadmin

```

---

### Post by colau on 2009-05-09
Bump

---

### Post by _Purple_ on 2009-05-19
Have you managed to solve your problem? If not, try these commands
```
sudo dpkg --configure -a
sudo apt-get -f install
```

---

### Post by colau on 2009-05-19
> **_Purple_ said:**
> Have you managed to solve your problem? If not, try these commands
```
sudo dpkg --configure -a
sudo apt-get -f install
```
I had to reinstall ubuntu 9.04.

---

