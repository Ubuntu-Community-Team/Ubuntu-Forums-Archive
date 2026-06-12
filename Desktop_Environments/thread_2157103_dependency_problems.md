---
title: "dependency problems"
date: 2013-06-24
forum: Desktop Environments
---

### Post by veledrom on 2013-06-24
Hi,

 Everytime I try to _ap-get install_, I get dependency problems. I cannot install anything. Example _php-pear php5-dev_, _rabbitvcs-core rabbitvcs-nautilus rabbitvcs-cli_ and many more....

Is there any way of sorting out my Ubuntu 12.04. I think it is mess.

Thanks



```
jojo@ubuntu:~$ sudo apt-get install php-pear php5-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 php-pear : Depends: php5-cli but it is not going to be installed
 php5-dev : Depends: autoconf (>= 2.63) but it is not installable
            Depends: automake (>= 1.11) but it is not installable
            Depends: libtool (>= 2.2) but it is not installable
            Depends: shtool but it is not installable
E: Unable to correct problems, you have held broken packages.
jojo@ubuntu:~$
```

```

jojo@ubuntu:~$ sudo apt-get install rabbitvcs-core rabbitvcs-nautilus rabbitvcs-cli
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 rabbitvcs-core : Depends: python-svn (>= 1.7.2) but it is not installable
                  Depends: python-configobj (>= 4.4.0) but it is not installable
                  Depends: meld (>= 1.1.2) but it is not installable
                  Depends: ipython (>= 0.7.1) but it is not installable
                  Depends: python-dulwich (>= 0.6.1) but it is not installable
 rabbitvcs-nautilus : Depends: nautilus (< 1:3.0~) but 1:3.4.2-0ubuntu8 is to be installed
                      Depends: python-nautilus (>= 0.5.0~) but it is not installable
                      Depends: python-nautilus (< 1.0~) but it is not installable
E: Unable to correct problems, you have held broken packages.
jojo@ubuntu:~$
```

---

### Post by ajgreeny on 2013-06-24
Have you added any pps repos that have changed versions of anything that's causing you a problem?

---

### Post by veledrom on 2013-06-24
Highly likely yes....

---

