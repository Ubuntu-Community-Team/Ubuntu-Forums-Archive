---
title: "Cannot launch Frostwire...!"
date: 2009-04-17
forum: General Help
---

### Post by jason.b.c on 2009-04-17
just installed Frostwire , when i try to launch it i get this error message...

```
jason@HP-Vectra-VL:~$ locate frostwire
/usr/bin/frostwire
/usr/lib/frostwire
/usr/lib/frostwire/FrostWire.icns
/usr/lib/frostwire/FrostWire.jar
/usr/lib/frostwire/ProgressTabs.jar
/usr/lib/frostwire/aopalliance.jar
/usr/lib/frostwire/clink.jar
/usr/lib/frostwire/commons-codec-1.3.jar
/usr/lib/frostwire/commons-logging.jar
/usr/lib/frostwire/daap.jar
/usr/lib/frostwire/docs
/usr/lib/frostwire/forms.jar
/usr/lib/frostwire/foxtrot.jar
/usr/lib/frostwire/fw-irc.jar
/usr/lib/frostwire/gettext-commons.jar
/usr/lib/frostwire/guice-1.0.jar
/usr/lib/frostwire/hashes
/usr/lib/frostwire/httpclient-4.0-alpha3.jar
/usr/lib/frostwire/httpcore-4.0-beta2.jar
/usr/lib/frostwire/httpcore-nio-4.0-beta2.jar
/usr/lib/frostwire/httpcore-niossl-4.0-alpha7.jar
/usr/lib/frostwire/icu4j.jar
/usr/lib/frostwire/jaudiotagger.jar
/usr/lib/frostwire/jcraft.jar
/usr/lib/frostwire/jdic.jar
/usr/lib/frostwire/jdic_stub.jar
/usr/lib/frostwire/jflac.jar
/usr/lib/frostwire/jl.jar
/usr/lib/frostwire/jmdns.jar
/usr/lib/frostwire/jogg.jar
/usr/lib/frostwire/jorbis.jar
/usr/lib/frostwire/libjdic.so
/usr/lib/frostwire/libtray.so
/usr/lib/frostwire/log4j.jar
/usr/lib/frostwire/log4j.properties
/usr/lib/frostwire/looks.jar
/usr/lib/frostwire/lw-all.jar
/usr/lib/frostwire/messages.jar
/usr/lib/frostwire/mp3spi.jar
/usr/lib/frostwire/onion-common.jar
/usr/lib/frostwire/onion-fec.jar
/usr/lib/frostwire/pmf.ico
/usr/lib/frostwire/root
/usr/lib/frostwire/runFrostwire.sh
/usr/lib/frostwire/themes.jar
/usr/lib/frostwire/tritonus.jar
/usr/lib/frostwire/update.ver
/usr/lib/frostwire/vorbisspi.jar
/usr/lib/frostwire/docs/EULA.txt
/usr/lib/frostwire/docs/GPL.txt
/usr/lib/frostwire/root/magnet10
/usr/lib/frostwire/root/magnet10/badge.img
/usr/lib/frostwire/root/magnet10/canHandle.img
/usr/lib/frostwire/root/magnet10/limewire.gif
/usr/lib/frostwire/root/magnet10/options.js
/usr/lib/frostwire/root/magnet10/silentdetect.js
/usr/share/applications/frostwire.desktop
/usr/share/doc/frostwire
/usr/share/doc/frostwire/changelog
/usr/share/icons/hicolor/32x32/apps/frostwire.png
/usr/share/icons/hicolor/48x48/apps/frostwire.png
/usr/share/icons/hicolor/64x64/apps/frostwire.png
/var/lib/dpkg/info/frostwire.list
jason@HP-Vectra-VL:~$ /usr/bin/frostwire
HOSTNAME IS HP-Vectra-VL
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at http://www.java.com
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ls: cannot access /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
jason@HP-Vectra-VL:~$ 

```

Ok., so then thinking i didn't have the latest Java in here i skipped over to their site...         i followed the instructions...!!!!!


[http://java.com/en/download/help/5000010500.xml#selfextracting](http://java.com/en/download/help/5000010500.xml#selfextracting)


but Frostwire still is a no-go....


any ideas what the problem might be...?:(

---

### Post by taurus on 2009-04-17
Install sun java with
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```
When you get to the licensing screen, press the Tab key to highlight the <OK> and Return to accept it.

---

### Post by jason.b.c on 2009-04-17
> **taurus said:**
> Install sun java with
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```
When you get to the licensing screen, press the Tab key to highlight the <OK> and Return to accept it.

Thank You -----  i will try this right now....

---

### Post by jason.b.c on 2009-04-17
Ok , it still isn't much of a GO...

```
jason@HP-Vectra-VL:~$ sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[B]sun-java6-bin is already the newest version.
sun-java6-bin set to manually installed.
sun-java6-jre is already the newest version.
sun-java6-jre set to manually installed.
sun-java6-plugin is already the newest version[/B].
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
jason@HP-Vectra-VL:~$ **sudo apt-get upgrade sun-java6-bin sun-java6-jre sun-java6-plugin**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  tzdata
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 674kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com intrepid-updates/main tzdata 2009f-0ubuntu0.8.10 [674kB]
Fetched 674kB in 17s (38.7kB/s)                                                
Preconfiguring packages ...
(Reading database ... 205390 files and directories currently installed.)
Preparing to replace tzdata 2009d-0ubuntu0.8.10 (using .../tzdata_2009f-0ubuntu0.8.10_all.deb) ...
Unpacking replacement tzdata ...
Setting up tzdata (2009f-0ubuntu0.8.10) ...

Current default timezone: 'America/Chicago'
Local time is now:      Fri Apr 17 19:21:16 CDT 2009.
Universal Time is now:  Sat Apr 18 00:21:16 UTC 2009.
Run 'dpkg-reconfigure tzdata' if you wish to change it.


jason@HP-Vectra-VL:~$ 

```


tzdata.....????   what the hell..!

terminal output reads as already the newest versions , wich i had figured as much before i started...

any other suggestions...?

---

### Post by ddrichardson on 2009-04-17
If you installed Java manually, you might need to set the paths, there's a thread [here]("http://ubuntuforums.org/showthread.php?t=217936&highlight=classpath").

---

### Post by Mze on 2009-04-17
Run in terminal > java -version to see which version of Java the system is presently using. If version in use is less than 1.6 continue with the next command.

Run in terminal > sudo update-alternatives --config java

and select Java 1.6 at the prompt.

---

### Post by jason.b.c on 2009-04-17
> **Mze said:**
> Run in terminal  to see which version of Java the system is presently using. If version in use is less than 1.6 continue with the next command.

Run in terminal 

and select Java 1.6 at the prompt.

```
jason@HP-Vectra-VL:~$ java -version
java version "1.5.0"
gij (GNU libgcj) version 4.3.2

Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
jason@HP-Vectra-VL:~$ sudo update-alternatives --config java
[sudo] password for jason: 

There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/lib/jvm/java-6-sun/jre/bin/java
          2    /usr/bin/gij-4.2
          3    /usr/bin/gij-4.3
*+        4    /usr/lib/jvm/java-gcj/jre/bin/java

Press enter to keep the default[*], or type selection number: 1
Using '/usr/lib/jvm/java-6-sun/jre/bin/java' to provide 'java'.
jason@HP-Vectra-VL:~$ 

```

time for another go... :D

---

### Post by jason.b.c on 2009-04-17
downloading files and adjusting settings in frostwire right now.... :)

thanks everyone... :)

---

