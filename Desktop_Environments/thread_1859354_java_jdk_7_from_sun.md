---
title: "java jdk 7 from sun"
date: 2011-10-13
forum: Desktop Environments
---

### Post by boblizar on 2011-10-13
if you have not noticed, this is my ubuntu master thesis....
[http://ubuntuforums.org/showthread.php?t=1836890](http://ubuntuforums.org/showthread.php?t=1836890)
check it out and share it with your friends =)

this is to install java jdk and link the browser plugins.  i updated from ubuntu 10.10 to 11.04 and java blew up in the process.  i know the ubuntu devs are very busy with the nose picking competition so ill git er done myself and help u 2.  i download the tarball from [http://www.oracle.com/technetwork/java/javase/downloads/jdk-7u2-download-1377129.html](http://www.oracle.com/technetwork/java/javase/downloads/jdk-7u2-download-1377129.html) and use previous jdk explosion experience from this thread [http://ubuntuforums.org/showthread.php?t=1747116](http://ubuntuforums.org/showthread.php?t=1747116)  this is specific for 64 however 86 is very similar and i will cover the differences in the post below this one.

to start out we need to open terminal and move jdk to an appropriate location

press alt + f2

enter "gnome-terminal"

run

then drop this code to move the tarball from your download folder to a more appropriate place for system wide installation.

```

sudo mv /home/$USER/Downloads/jdk-7u2-linux-x64.tar.gz /usr/lib

```

now unpack the tarball, and blast the tarball off your system once unpacked.

drop this code

```

cd /usr/lib
sudo tar -xf jdk-7u2-linux-x64.tar.gz && sudo rm /usr/lib/jdk-7u2-linux-x64.tar.gz

```

nabbed and altered code from previous experience  run these lines 1 by 1

```

sudo ln -s /usr/lib/jdk1.7.0_02/ /usr/lib/java

sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/java/bin/java" 1

sudo update-alternatives --set java /usr/lib/java/bin/java

sudo update-alternatives --set java /usr/lib/java/bin/java

```

fresh install does not have a plugins directory for mozilla by default so make it if you do not have it

```

mkdir $HOME/.mozilla/plugins

```

and finally link your plugin to the browsers....  this line will fix java for your user, and will need re run for future users.

```

ln -s /usr/lib/java/jre/lib/amd64/libnpjp2.so /home/$USER/.mozilla/plugins/

sudo rm /usr/lib/mozilla/plugins/libjavaplugin.so

sudo ln -s /usr/lib/java/jre/lib/amd64/libnpjp2.so /usr/lib/mozilla/plugins/libjavaplugin.so

```

---

### Post by boblizar on 2011-10-13
for 86 it should replace the tarball name and final link location

code block 1 replace with

```

sudo mv /home/$USER/Downloads/jdk-7u2-linux-i586.tar.gz /usr/lib

```

code block 2 replace with

```

cd /usr/lib
sudo tar -xf jdk-7u2-linux-i586.tar.gz && sudo rm /usr/lib/jdk-7u2-linux-i586.tar.gz

```

middle code block should be fine...  and the final code block replace with

```

ln -s /usr/lib/java/jre/lib/i386/libnpjp2.so /home/$USER/.mozilla/plugins/

sudo rm /usr/lib/mozilla/plugins/libjavaplugin.so

sudo ln -s /usr/lib/java/jre/lib/i386/libnpjp2.so /usr/lib/mozilla/plugins/libjavaplugin.so

```

---

