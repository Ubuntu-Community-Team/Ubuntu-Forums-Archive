---
title: "ubuntu with a  cvs installation of spamd not upgrading"
date: 2006-10-01
forum: Desktop Environments
---

### Post by MegaHz on 2006-10-01
hi experts,
I have a dapper upgraded to edgy beta using the upgrade-manager..

before the upgrade I have installed spamd from a cvs (I dont know much about cvs but I found an instalation guide from the net). 

anyway my problem now is that the system is giving errors on apt-get upgrade about spamd, and not upgrade, see the following:

------------------------------------------------------

megahz@megahz-desktop:~/paros$ sudo apt-get upgrade
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  hpijs libggi2 listen mplayer python-adns python-clientcookie python-crypto python-gadfly python-htmlgen python-htmltmpl python-imaging
  python-imaging-sane python-jabber python-kjbuckets python-ldap python-mysqldb python-pam python-pexpect python-pgsql python-pylibacl python-pyopenssl
  python-pyxattr python-reportlab python-simpletal python-soappy python-sqlite python-syck python-xmpp
0 upgraded, 0 newly installed, 0 to remove and 28 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up spampd (2.30-11) ...
An override for "/var/cache/spampd" already exists, aborting
Warning: statoverride couldn't be created for /var/cache/spampd
An override for "/etc/spampd.conf" already exists, aborting
Warning: statoverride couldn't be created for /etc/spampd.conf
 * ERROR: Insufficient privileges. Retry as root
invoke-rc.d: initscript spampd, action "start" failed.
dpkg: error processing spampd (--configure):
 subprocess post-installation script returned error exit status 4
Errors were encountered while processing:
 spampd
E: Sub-process /usr/bin/dpkg returned an error code (1)
megahz@megahz-desktop:~/paros$ 
----------------------------------------------------------------

Is there a way to solve the above problem, so that my machine can start upgrading again?

what is the best solution? uninstall spamd? I dont even need it, because I am using spamassassin in evolution.

thanks in advance

---

### Post by MegaHz on 2006-10-02
anybody?

---

### Post by chenggao on 2006-10-02
I had the same problem  after upgrading from dapper to edgy.

At last I tried the solution as following and it worked:

in terminal, go to /etc/init.d, and do:
sudo rm spampd

and then 
sudo aptitude remove spampd

---

