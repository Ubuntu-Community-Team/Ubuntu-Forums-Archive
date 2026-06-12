---
title: "Installation Error: Trying other mirror."
date: 2018-01-26
forum: Fedora/RedHat and derivatives
---

### Post by linux-newbie2 on 2018-01-26
Hi,
I am very new to linux (centos 7) and while installing some softwares/packages I end up always with something like this error which seems trying to download some package from internet but didn't reached:

[root@localhost ~]# yum update -y && reboot
.
.
.

firefox-52.6.0-1.el7.centos.x8 FAILED                                          
[http://mirror.fra10.de.leaseweb.net/centos/7.4.1708/updates/x86_64/Packages/firefox-52.6.0-1.el7.centos.x86_64.rpm:](http://mirror.fra10.de.leaseweb.net/centos/7.4.1708/updates/x86_64/Packages/firefox-52.6.0-1.el7.centos.x86_64.rpm:) [Errno 12] Timeout on [http://mirror.fra10.de.leaseweb.net/centos/7.4.1708/updates/x86_64/Packages/firefox-52.6.0-1.el7.centos.x86_64.rpm:](http://mirror.fra10.de.leaseweb.net/centos/7.4.1708/updates/x86_64/Packages/firefox-52.6.0-1.el7.centos.x86_64.rpm:) (28, 'Operation too slow. Less than 1000 bytes/sec transferred the last 30 seconds')
Trying other mirror.
java-1.8.0-openjdk-headless-1. FAILED                                          
[http://mirror.fra10.de.leaseweb.net/centos/7.4.1708/updates/x86_64/Packages/java-1.8.0-openjdk-headless-1.8.0.161-0.b14.el7_4.x86_64.rpm:](http://mirror.fra10.de.leaseweb.net/centos/7.4.1708/updates/x86_64/Packages/java-1.8.0-openjdk-headless-1.8.0.161-0.b14.el7_4.x86_64.rpm:) [Errno 12] Timeout on [http://mirror.fra10.de.leaseweb.net/centos/7.4.1708/updates/x86_64/Packages/java-1.8.0-openjdk-headless-1.8.0.161-0.b14.el7_4.x86_64.rpm:](http://mirror.fra10.de.leaseweb.net/centos/7.4.1708/updates/x86_64/Packages/java-1.8.0-openjdk-headless-1.8.0.161-0.b14.el7_4.x86_64.rpm:) (28, 'Operation too slow. Less than 1000 bytes/sec transferred the last 30 seconds')
Trying other mirror.
firefox-52.6.0-1.el7.centos.x8 FAILED                                          
[http://mirror.eu.oneandone.net/linux/distributions/centos/7.4.1708/updates/x86_64/Packages/firefox-52.6.0-1.el7.centos.x86_64.rpm:](http://mirror.eu.oneandone.net/linux/distributions/centos/7.4.1708/updates/x86_64/Packages/firefox-52.6.0-1.el7.centos.x86_64.rpm:) [Errno 12] Timeout on [http://mirror.eu.oneandone.net/linux/distributions/centos/7.4.1708/updates/x86_64/Packages/firefox-52.6.0-1.el7.centos.x86_64.rpm:](http://mirror.eu.oneandone.net/linux/distributions/centos/7.4.1708/updates/x86_64/Packages/firefox-52.6.0-1.el7.centos.x86_64.rpm:) (28, 'Operation too slow. Less than 1000 bytes/sec transferred the last 30 seconds')
Trying other mirror.
java-1.8.0-openjdk-headless-1. FAILED                                          
[http://mirror.eu.oneandone.net/linux/distributions/centos/7.4.1708/updates/x86_64/Packages/java-1.8.0-openjdk-headless-1.8.0.161-0.b14.el7_4.x86_64.rpm:](http://mirror.eu.oneandone.net/linux/distributions/centos/7.4.1708/updates/x86_64/Packages/java-1.8.0-openjdk-headless-1.8.0.161-0.b14.el7_4.x86_64.rpm:) [Errno 12] Timeout on [http://mirror.eu.oneandone.net/linux/distributions/centos/7.4.1708/updates/x86_64/Packages/java-1.8.0-openjdk-headless-1.8.0.161-0.b14.el7_4.x86_64.rpm:](http://mirror.eu.oneandone.net/linux/distributions/centos/7.4.1708/updates/x86_64/Packages/java-1.8.0-openjdk-headless-1.8.0.161-0.b14.el7_4.x86_64.rpm:) (28, 'Operation too slow. Less than 1000 bytes/sec transferred the last 30 seconds')
Trying other mirror.
firefox-52.6.0-1.el7.centos.x8 FAILED                                          
[http://ftp.hosteurope.de/mirror/centos.org/7.4.1708/updates/x86_64/Packages/firefox-52.6.0-1.el7.centos.x86_64.rpm:](http://ftp.hosteurope.de/mirror/centos.org/7.4.1708/updates/x86_64/Packages/firefox-52.6.0-1.el7.centos.x86_64.rpm:) [Errno 12] Timeout on [http://ftp.hosteurope.de/mirror/centos.org/7.4.1708/updates/x86_64/Packages/firefox-52.6.0-1.el7.centos.x86_64.rpm:](http://ftp.hosteurope.de/mirror/centos.org/7.4.1708/updates/x86_64/Packages/firefox-52.6.0-1.el7.centos.x86_64.rpm:) (28, 'Operation too slow. Less than 1000 bytes/sec transferred the last 30 seconds')
Trying other mirror.
java-1.8.0-openjdk-headless-1. FAILED                                          
[http://mirror.maeh.org/centos/7.4.1708/updates/x86_64/Packages/java-1.8.0-openjdk-headless-1.8.0.161-0.b14.el7_4.x86_64.rpm:](http://mirror.maeh.org/centos/7.4.1708/updates/x86_64/Packages/java-1.8.0-openjdk-headless-1.8.0.161-0.b14.el7_4.x86_64.rpm:) [Errno 12] Timeout on [http://mirror.maeh.org/centos/7.4.1708/updates/x86_64/Packages/java-1.8.0-openjdk-headless-1.8.0.161-0.b14.el7_4.x86_64.rpm:](http://mirror.maeh.org/centos/7.4.1708/updates/x86_64/Packages/java-1.8.0-openjdk-headless-1.8.0.161-0.b14.el7_4.x86_64.rpm:) (28, 'Operation too slow. Less than 1000 bytes/sec transferred the last 30 seconds')
Trying other mirror.
firefox-52.6.0-1.el7.centos.x8 FAILED                                          
[http://de.mirror.guru/centos/7.4.1708/updates/x86_64/Packages/firefox-52.6.0-1.el7.centos.x86_64.rpm:](http://de.mirror.guru/centos/7.4.1708/updates/x86_64/Packages/firefox-52.6.0-1.el7.centos.x86_64.rpm:) [Errno 12] Timeout on [http://de.mirror.guru/centos/7.4.1708/updates/x86_64/Packages/firefox-52.6.0-1.el7.centos.x86_64.rpm:](http://de.mirror.guru/centos/7.4.1708/updates/x86_64/Packages/firefox-52.6.0-1.el7.centos.x86_64.rpm:) (28, 'Operation too slow. Less than 1000 bytes/sec transferred the last 30 seconds')
Trying other mirror.
java-1.8.0-openjdk-headless-1. FAILED                                          
[http://mirror.cuegee.de/centos/7.4.1708/updates/x86_64/Packages/java-1.8.0-openjdk-headless-1.8.0.161-0.b14.el7_4.x86_64.rpm:](http://mirror.cuegee.de/centos/7.4.1708/updates/x86_64/Packages/java-1.8.0-openjdk-headless-1.8.0.161-0.b14.el7_4.x86_64.rpm:) [Errno 12] Timeout on [http://mirror.cuegee.de/centos/7.4.1708/updates/x86_64/Packages/java-1.8.0-openjdk-headless-1.8.0.161-0.b14.el7_4.x86_64.rpm:](http://mirror.cuegee.de/centos/7.4.1708/updates/x86_64/Packages/java-1.8.0-openjdk-headless-1.8.0.161-0.b14.el7_4.x86_64.rpm:) (28, 'Operation too slow. Less than 1000 bytes/sec transferred the last 30 seconds')
Trying other mirror.
firefox-52.6.0-1.el7.centos.x8 FAILED                                          
[http://centos.mirror.net-d-sign.de/7.4.1708/updates/x86_64/Packages/firefox-52.6.0-1.el7.centos.x86_64.rpm:](http://centos.mirror.net-d-sign.de/7.4.1708/updates/x86_64/Packages/firefox-52.6.0-1.el7.centos.x86_64.rpm:) [Errno 12] Timeout on [http://centos.mirror.net-d-sign.de/7.4.1708/updates/x86_64/Packages/firefox-52.6.0-1.el7.centos.x86_64.rpm:](http://centos.mirror.net-d-sign.de/7.4.1708/updates/x86_64/Packages/firefox-52.6.0-1.el7.centos.x86_64.rpm:) (28, 'Operation too slow. Less than 1000 bytes/sec transferred the last 30 seconds')
Trying other mirror.
java-1.8.0-openjdk-headless-1. FAILED                                          
[http://ftp.wrz.de/pub/CentOS/7.4.1708/updates/x86_64/Packages/java-1.8.0-openjdk-headless-1.8.0.161-0.b14.el7_4.x86_64.rpm:](http://ftp.wrz.de/pub/CentOS/7.4.1708/updates/x86_64/Packages/java-1.8.0-openjdk-headless-1.8.0.161-0.b14.el7_4.x86_64.rpm:) [Errno 12] Timeout on [http://ftp.wrz.de/pub/CentOS/7.4.1708/updates/x86_64/Packages/java-1.8.0-openjdk-headless-1.8.0.161-0.b14.el7_4.x86_64.rpm:](http://ftp.wrz.de/pub/CentOS/7.4.1708/updates/x86_64/Packages/java-1.8.0-openjdk-headless-1.8.0.161-0.b14.el7_4.x86_64.rpm:) (28, 'Operation too slow. Less than 1000 bytes/sec transferred the last 30 seconds')
Trying other mirror.
.
.
.
Error downloading packages:
  firefox-52.6.0-1.el7.centos.x86_64: [Errno 256] No more mirrors to try.
  1:java-1.8.0-openjdk-headless-1.8.0.161-0.b14.el7_4.x86_64: [Errno 256] No more mirrors to try.

[root@localhost ~]# 


I don't know whether it is due to firewall or something else. 
can anybody please help?

---

### Post by jeremy31 on 2018-01-26
Moved to Fedora, Red Hat and derivatives

---

