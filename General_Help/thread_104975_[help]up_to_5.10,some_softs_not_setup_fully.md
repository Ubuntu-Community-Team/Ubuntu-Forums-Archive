---
title: "[help]up to 5.10,some softs not setup fully???"
date: 2005-12-17
forum: General Help
---

### Post by survival on 2005-12-17
i did like this:
sudo -s -H
apt-get update
apt-get dist-upgrade

and then when last ,i got this information below:
--------------------------------------------------------------------------------------
root@ubuntu:/var/cache/apt/archives # apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up postfix (2.2.4-1ubuntu2) ...

Postfix configuration was untouched.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
 * Starting Postfix Mail Transport Agent... postfix/postfix-script: fatal: the Postfix mail system is already running
                                                                                                                      [fail]
invoke-rc.d: initscript postfix, action "start" failed.
dpkg: error processing postfix (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mailx:
 mailx depends on postfix | mail-transport-agent; however:
  Package postfix is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing mailx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mutt:
 mutt depends on postfix | mail-transport-agent; however:
  Package postfix is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing mutt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-core:
 lsb-core depends on postfix | mail-transport-agent; however:
  Package postfix is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing lsb-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-graphics:
 lsb-graphics depends on lsb-core; however:
  Package lsb-core is not configured yet.
dpkg: error processing lsb-graphics (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-cxx:
 lsb-cxx depends on lsb-core; however:
  Package lsb-core is not configured yet.
dpkg: error processing lsb-cxx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb:
 lsb depends on lsb-core; however:
  Package lsb-core is not configured yet.
 lsb depends on lsb-graphics; however:
  Package lsb-graphics is not configured yet.
 lsb depends on lsb-cxx; however:
  Package lsb-cxx is not configured yet.
dpkg: error processing lsb (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 postfix
 mailx
 mutt
 lsb-core
 lsb-graphics
 lsb-cxx
 lsb
E: Sub-process /usr/bin/dpkg returned an error code (1)
----------------------------------------------------------------------------

please help me go on my upgrade,and i want to install some other ttf,but cann't go on....

now  i am on line ,waitng for your help ..thank you very much!

---

### Post by survival on 2005-12-17
please , i am waiting  here now ...someone can help me??

---

### Post by survival on 2005-12-17
[QUOTE=survival]please , i am waiting  here now ...someone can help me??[/QUOTE]

is there someone can help me solve this problem???????

---

### Post by survival on 2005-12-17
done!

i am just a new user of ubuntu.so this question i mentioned above is really stupid....

ok, i take some actions like this:
1, because the info about my problem given by ubuntu itself, i consider these sofewares just only install partially,so i remove all of them.
    dpkg -r postfix
    dpkg -r lsb
    dpkg -r lsb-cxx
    dpkg -r lsb-graphics
    dpkg  -r lsb-core
    dpkg   -r mutt 
    dpkg   -r mailx
2,then, i redownload all of them ,just because i delete all of their deb files in folde 
/var/cache/apt/archives .so the commands  are:
    apt-get install postfix
    apt-get install lsb   
    ...
after that ,everything is perfect. haha :)

---

