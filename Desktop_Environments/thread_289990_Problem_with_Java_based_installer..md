---
title: "Problem with Java based installer."
date: 2006-10-31
forum: Desktop Environments
---

### Post by acascianelli on 2006-10-31
I installed this fine on my Dapper setup earlier this week but I'm getting the following errors in Edgy...

acascianelli@Edgy:~/Downloads/Adonis Client/Unix/Linux$ sh Install.bin 
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
nawk: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
hostname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

Launching installer...

grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/tmp/install.dir.13060/Linux/resource/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory
acascianelli@Edgy:~/Downloads/Adonis Client/Unix/Linux$ 

...I have a feeling this is an easy fix with me not having a certain package installed that I need.  Can somebody please help me out.  I already have build-essential installed.

UPDATE:

It looks worse than I expected, here is some other people with a similar problem...

[http://www.ubuntuforums.org/showthread.php?t=260107&highlight=libc.so.6%3A+cannot+open+shared+object+file%3A+No+such+file+OR+directory](http://www.ubuntuforums.org/showthread.php?t=260107&highlight=libc.so.6%3A+cannot+open+shared+object+file%3A+No+such+file+OR+directory)

---

### Post by acascianelli on 2006-10-31
I found a fix but I don't like it...

cp Install.bin Install.bak
cat Install.bak | sed "s/export LD_ASSUME_KERNEL/#xport LD_ASSUME_KERNEL/" > Install.bin
rm Install.bak

You have to do that to the installer, and the executable once its installed.

---

### Post by acascianelli on 2006-11-01
Better explanation of similar problem...

[http://www.ubuntuforums.org/showpost.php?p=1337016&postcount=8](http://www.ubuntuforums.org/showpost.php?p=1337016&postcount=8)

Basically, in any Java program, make sure that there is no lines reading "export LD_ASSUME_KERNEL", and if there is just change the first character 'e' to a # to comment it out.  Hopefully this will be fixed in an update sometime soon.

---

