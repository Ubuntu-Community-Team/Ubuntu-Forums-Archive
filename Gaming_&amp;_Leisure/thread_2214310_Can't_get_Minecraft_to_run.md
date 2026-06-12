---
title: "Can't get Minecraft to run"
date: 2014-03-31
forum: Gaming &amp; Leisure
---

### Post by trotter-danny on 2014-03-31
I am on Ubuntu 13.04 and have followed instructions on how to get Java installed and still am getting this error 

Error occurred during initialization of VM
java/lang/ClassNotFoundException: error in opening JAR file <Zip file open error> /usr/local/java/jre1.7.0_51/lib/rt.jar

I did these steps to clear out any old java:
[INDENT] sudo rm /var/lib/dpkg/info/oracle-java7-installer*
sudo apt-get purge oracle-java7-installer*
sudo rm /etc/apt/sources.list.d/*java*
sudo apt-get update
[/INDENT]Then I did these steps to install it:
[INDENT] sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer

[/INDENT]Here is what I got:

```
playroom@Playroom-Ubuntu:~/Desktop$ sudo apt-get install oracle-java7-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  binfmt-support visualvm ttf-baekmuk ttf-unfonts ttf-unfonts-core
  ttf-kochi-gothic ttf-sazanami-gothic ttf-kochi-mincho ttf-sazanami-mincho
  ttf-arphic-uming
The following NEW packages will be installed:
  oracle-java7-installer
0 upgraded, 1 newly installed, 0 to remove and 102 not upgraded.
Need to get 0 B/18.6 kB of archives.
After this operation, 193 kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously unselected package oracle-java7-installer.
(Reading database ... 194161 files and directories currently installed.)
Unpacking oracle-java7-installer (from .../oracle-java7-installer_7u51-0~webupd8~4_all.deb) ...
oracle-license-v1-1 license has already been accepted
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support ...
Processing triggers for shared-mime-info ...
Setting up oracle-java7-installer (7u51-0~webupd8~4) ...
Installing from local file /var/cache/oracle-jdk7-installer/jdk-7u51-linux-x64.tar.gz
Removing outdated cached downloads...
Oracle JDK 7 installed
Oracle JRE 7 browser plugin installed
playroom@Playroom-Ubuntu:~/Desktop$ java -version
[B]Error occurred during initialization of VM
java/lang/ClassNotFoundException: error in opening JAR file <Zip file open error> /usr/local/java/jre1.7.0_51/lib/rt.jar[/B]

```

Any idea why this is happening?  When I go to start Minecraft I get:

playroom@Playroom-Ubuntu:~/Desktop$ java -jar Minecraft.jar
Error occurred during initialization of VM
java/lang/ClassNotFoundException: error in opening JAR file <Zip file open error> /usr/local/java/jre1.7.0_51/lib/rt.jar

---

### Post by mörgæs on 2014-04-01
13.04 is unsupported. Best is to begin with a fresh install of 13.10.

Please post again when that is running.

---

