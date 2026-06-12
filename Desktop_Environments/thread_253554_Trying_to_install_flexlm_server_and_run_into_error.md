---
title: "Trying to install flexlm server and run into error"
date: 2006-09-08
forum: Desktop Environments
---

### Post by Saubazi on 2006-09-08
I am trying to install flexlm server on my box but I run
into problem:

I get:

jykke@Dildo:~$ sudo sh /opt/linux32/product/UNIX/Disk1/InstData/NoVM/install.bin
Preparing to install...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
/opt/linux32/product/UNIX/Disk1/InstData/NoVM/install.bin: line 2089: strings: command not found


line 2089 is the one with nptl and so on so obviously I am running sh script but strings command is not recognized?

if [ `uname` = "Linux" ]; then
        debugOut "checking for NPTL + JVM vulernability..."
        #check libc to see if it was compiled with NPTL
        nptl="`strings /lib/libc.so.6 | grep -i nptl`"

beats me I launch the stuff but now I don't have a clue what to do next...

---

### Post by pould on 2006-09-25
It seems you're missing 'strings' utility. You should probably just go install it from your disitribution. That will probably solve it easily.

If you need tool to do statistics on your flexlm license server you should look into License Statistics. It's a really inexpensive tool for monitoring the usage of your server. Well recommended... [http://www.x-formation.com/license_statistics/index.html](http://www.x-formation.com/license_statistics/index.html)

Good luck!

-- Poul

---

### Post by lamego on 2006-09-25
The "string" utility is provided by the binutils package.

---

