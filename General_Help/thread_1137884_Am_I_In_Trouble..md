---
title: "Am I In Trouble."
date: 2009-04-26
forum: General Help
---

### Post by gemmink on 2009-04-26
I upgraded to the new version of ubuntu and it installed as planned. However as it was restarting I shut it off prematurely and now the update manager says that one of the updates cannot be completed. Should I just reinstall the operating system?

---

### Post by gta117 on 2009-04-26
first, back up anything if you have not already.

2nd, see if you can re-download 9.04 and then install it like that. (like a cd or through the updater.)

Or, if you want, try and re-install it. Best way is to: put the iso of 9.04 on a cd. That way if anything is wrong, it will not be re-put on. It also prevents you from having to RE-install 9 when say, you have a cd thats 7.


link for desktop: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Peace!

-gta117

---

### Post by gemmink on 2009-04-26
> **gta117 said:**
> first, back up anything if you have not already.

2nd, see if you can re-download 9.04 and then install it like that. (like a cd or through the updater.)

Or, if you want, try and re-install it. Best way is to: put the iso of 9.04 on a cd. That way if anything is wrong, it will not be re-put on. It also prevents you from having to RE-install 9 when say, you have a cd thats 7.


link for desktop: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Peace!

-gta117

Do I really need to reinstall it is my question though.

---

### Post by Tipped OuT on 2009-04-26
Yes you do. You permanently broke an update. This happens with me sometimes...*sigh* :(

---

### Post by ad_267 on 2009-04-26
You might not need to. It depends on what message you're getting and what the problem is.

Try entering "sudo apt-get update && sudo apt-get check && sudo apg-get upgrade" in a terminal and post the output here.

---

### Post by agim on 2009-04-26
You probably don't. Post that output, most things do not require a reinstall.

---

### Post by gemmink on 2009-04-26
> **ad_267 said:**
> You might not need to. It depends on what message you're getting and what the problem is.

Try entering "sudo apt-get update && sudo apt-get check && sudo apg-get upgrade" in a terminal and post the output here.

michael@michael-laptop:~$ sudo apt-get update && sudo apt-get check && sudo apt-get upgrade
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-proposed Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-proposed/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-proposed/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-proposed/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-proposed/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security Release
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-proposed Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Sources                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/main Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-proposed/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-proposed/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-proposed/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-proposed/universe Packages
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  brasero liblucene2-java
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

---

### Post by ad_267 on 2009-04-26
Try "sudo apt-get dist-upgrade"

---

### Post by gemmink on 2009-04-26
> **ad_267 said:**
> Try "sudo apt-get dist-upgrade"

michael@michael-laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  libdb4.5-java
The following NEW packages will be installed:
  libdb4.6-java libdb4.6-java-gcj
The following packages have been kept back:
  brasero
The following packages will be upgraded:
  liblucene2-java
1 upgraded, 2 newly installed, 1 to remove and 1 not upgraded.
Need to get 0B/3175kB of archives.
After this operation, 3097kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 209178 files and directories currently installed.)
Preparing to replace liblucene2-java 2.3.2+ds1-1ubuntu1 (using .../liblucene2-java_2.4.0+ds1-5ubuntu1_all.deb) ...
Unpacking replacement liblucene2-java ...
Processing triggers for man-db ...
(Reading database ... 209179 files and directories currently installed.)
Removing libdb4.5-java ...
Selecting previously deselected package libdb4.6-java.
(Reading database ... 209173 files and directories currently installed.)
Unpacking libdb4.6-java (from .../libdb4.6-java_4.6.21-12_i386.deb) ...
Selecting previously deselected package libdb4.6-java-gcj.
Unpacking libdb4.6-java-gcj (from .../libdb4.6-java-gcj_4.6.21-12_i386.deb) ...
Setting up libdb4.6-java (4.6.21-12) ...
Setting up liblucene2-java (2.4.0+ds1-5ubuntu1) ...
Setting up libdb4.6-java-gcj (4.6.21-12) ...

---

### Post by ad_267 on 2009-04-26
Ok try "sudo apt-get install brasero"

---

