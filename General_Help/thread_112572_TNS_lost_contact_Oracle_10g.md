---
title: "TNS: lost contact Oracle 10g"
date: 2006-01-04
forum: General Help
---

### Post by tenaciousd on 2006-01-04
I'm running Ubuntu Breezy Badger and i'm using ([http://csee.wvu.edu/~ccole/oracle10g-ubuntu](http://csee.wvu.edu/~ccole/oracle10g-ubuntu)) as the install guide for Oracle 10g. 

I got through the software install and now Database Configuration Assistant kicks off to create the sample database. I immediately get a popup error "TNS: lost contact" and  I cannot proceed.  The software install ran clean until it tries to use DBCA.

I cancelled out of the autoinstaller and then kickoff DBCA separatly. The same thing happens. Has anyone seen this or does anyone have suggestions on where to troublshoot?  I can ping the localhost.

Any help would be greatly appreciated.

---

### Post by lnxpwr on 2006-01-08
hi,
how many memory do you have, and did you configure your sysctl.conf well.
had the same problem/error messages and in my place it was not a TNS problem, it was a missconfigured sysctl.
greetinx
pete

---

### Post by ape on 2006-01-08
What message (if any) do you get back when you attempt to run `lsnrctl start` from $ORACLE_HOME/bin?

Make sure that you have a proper loopback entry in your /etc/hosts file.

---

### Post by lnxpwr on 2006-01-08
hi,
the error messages was "TNS-xxxx lost connection to host....." something like that. than I created the db manually and used "netca" for build up the networking stuff
greetinx
p.

---

### Post by tenaciousd on 2006-01-09
Thanks for the replies.. i have FINALLY got Oracle installed.  The TNS: Lost Contact error turned out the result of a missing package (grrrr..).  After having so much trouble using DBCA i tried launching sqlplus command line and i got a more descriptive error msg regarding the libaio library. 

I installed libaio1 and libaio-dev packages and then was able to move on.  I soon hit an oracle error "insufficient privaliges"  during the database creation.  This was because didn't run DBCA as the 'oracle' user (i thought my current user had the same privaleges but something must have been different).  After those changes were made i installed completely clean!!!

---

### Post by lnxpwr on 2006-01-10
Hi,
greate !!!! Found out also that the most problems are caused by missing packages. Here is my list which worked for me to install 10g:
-gcc 
-make 
-binutils 
-lesstif2 libc6 
-libc6-dev 
-rpm 
-libaio 
-libaio-dev 
-libstdc++5 l
-ibstdc++5-3.3-dev 

What you think about of creating a "preinstallation script" ?
greetinx
pete

---

