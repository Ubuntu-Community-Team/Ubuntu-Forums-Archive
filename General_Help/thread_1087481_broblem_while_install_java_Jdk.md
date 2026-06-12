---
title: "broblem while install java Jdk"
date: 2009-03-05
forum: General Help
---

### Post by anyone2009 on 2009-03-05
hi ,,

i'm a beginner ubuntu user 

i'm java programmer 

when i try to install java Jdk 
i follow a topic frome this blog 
[http://www.mkyong.com/java/how-to-install-java-jdk-on-ubuntu-linux/](http://www.mkyong.com/java/how-to-install-java-jdk-on-ubuntu-linux/)

i have abroblem 

that's it 
```
mohamed@mohamed-desktop:~$ sudo apt-get install sun-java6-jdk sun-java6-jre
[sudo] password for mohamed: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libpopt-dev liborbit2-dev libperl-dev automake1.7 libtasn1-3-dev
  libaudiofile-dev libsoup2.4-dev libgpg-error-dev libebook1.2-dev
  libsilc-1.1-2-dev libcamel1.2-dev check libnm-util-dev libncursesw5-dev
  libgcrypt11-dev m4 libsqlite3-dev autoconf libebackend1.2-dev libzephyr-dev
  libsasl2-dev libavahi-client-dev tcl8.4-dev libnss3-dev
  libstartup-notification0-dev cdbs intltool doxygen libbonobo2-dev fdupes
  libmeanwhile-dev libgnutls-dev x11proto-scrnsaver-dev tk8.4-dev
  libdbus-1-dev libxt-dev libgadu-dev libnspr4-dev libidl-dev libesd0-dev
  libedata-book1.2-dev libdbus-glib-1-dev tcl8.4 tcl8.5 libgnomevfs2-dev tk8.4
  libgconf2-dev libedataserver1.2-dev libselinux1-dev libgstreamer0.10-dev
  libgtkspell-dev libgnome2-dev orbit2 libavahi-glib-dev libavahi-common-dev
  network-manager-dev libsepol1-dev libxss-dev liblaunchpad-integration-dev
  libenchant-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  sun-java6-bin
Suggested packages:
  sun-java6-demo sun-java6-doc sun-java6-source sun-java6-plugin
  ia32-sun-java6-plugin sun-java6-fonts
The following NEW packages will be installed
  sun-java6-bin sun-java6-jdk sun-java6-jre
0 upgraded, 3 newly installed, 0 to remove and 216 not upgraded.
Need to get 0B/52.0MB of archives.
After this operation, 155MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package sun-java6-jre.
(Reading database ... 119714 files and directories currently installed.)
Unpacking sun-java6-jre (from .../sun-java6-jre_6-10-0ubuntu2_all.deb) ...
sun-dlj-v1-1 license has already been accepted
Selecting previously deselected package sun-java6-bin.
Unpacking sun-java6-bin (from .../sun-java6-bin_6-10-0ubuntu2_i386.deb) ...
sun-dlj-v1-1 license has already been accepted
Selecting previously deselected package sun-java6-jdk.
Unpacking sun-java6-jdk (from .../sun-java6-jdk_6-10-0ubuntu2_i386.deb) ...
sun-dlj-v1-1 license has already been accepted
Processing triggers for doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
Setting up sun-java6-bin (6-10-0ubuntu2) ...

Setting up sun-java6-jre (6-10-0ubuntu2) ...

Setting up sun-java6-jdk (6-10-0ubuntu2) ...

mohamed@mohamed-desktop:~$ 

```

i think that's is the broblem 
Processing triggers for doc-base ...
Processing 1 added doc-base file(s)...

and i'm sorry because i have a weak English 

:(

---

### Post by ju2wheels on 2009-03-05
Theres no problem there. What problem are you having? The install looks like it worked fine to me.

And I wouldnt follow all the steps in that tutorial, as exporting JAVA_HOME is not always necessary and the way it suggests to do it is wrong anyway because its hard coding it to a specific version of java instead of using the generic path. So if an upgrade comes along it might cause you problems later if your applications are actually using it.

Follow these directions in my older post (note: I am assuming Ubuntu 8.04): [http://ubuntuforums.org/showpost.php?p=5959370&postcount=2](http://ubuntuforums.org/showpost.php?p=5959370&postcount=2)

---

### Post by abhishek.malhotra35 on 2009-03-05
The java is installed correctly. The issue is with setting the environment variables. You need to add java bin path to PATH and java lib path to CLASSPATH. Export the above paths and java will work as usual.

---

### Post by anyone2009 on 2009-03-05
> **ju2wheels said:**
> Theres no problem there. What problem are you having? The install looks like it worked fine to me.

And I wouldnt follow all the steps in that tutorial, as exporting JAVA_HOME is not always necessary and the way it suggests to do it is wrong anyway because its hard coding it to a specific version of java instead of using the generic path. So if an upgrade comes along it might cause you problems later if your applications are actually using it.

Follow these directions in my older post (note: I am assuming Ubuntu 8.04): [http://ubuntuforums.org/showpost.php?p=5959370&postcount=2](http://ubuntuforums.org/showpost.php?p=5959370&postcount=2)

thank's alot 
but it not work 

~$ java -version
java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) Client VM (build 11.0-b15, mixed mode, sharing)

where is the Jdk ?
,,
i do this step 
Once you complete that you want to add the path listed above next to java-6-sun to the /etc/jvm as the first line

but it's not work :(

---

### Post by anyone2009 on 2009-03-05
> **abhishek.malhotra35 said:**
> The java is installed correctly. The issue is with setting the environment variables. You need to add java bin path to PATH and java lib path to CLASSPATH. Export the above paths and java will work as usual.

thank's alot 
but ,
can you explain how to do that plz?

---

### Post by ju2wheels on 2009-03-05
> **anyone2009 said:**
> thank's alot 
but it not work 

~$ java -version
java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) Client VM (build 11.0-b15, mixed mode, sharing)

i do this step 
Once you complete that you want to add the path listed above next to java-6-sun to the /etc/jvm as the first line

but it's not work :(

Did you run "update-java-alternatives -s java-6-sun" after you updated the /etc/jvm file?

That output is correct, I still dont understand why you think something is wrong. Have you tried compiling a java program?

---

### Post by ju2wheels on 2009-03-05
> **abhishek.malhotra35 said:**
> The java is installed correctly. The issue is with setting the environment variables. You need to add java bin path to PATH and java lib path to CLASSPATH. Export the above paths and java will work as usual.

That is not necessary, as that is what update-java-alternatives is for, which is the recommended way as it also updates the paths for all the other components of the java environment package in use.

---

### Post by abhishek.malhotra35 on 2009-03-05
From the command line execute the following statement.
export PATH=$PATH:/(where your java is installed)/bin
export CLASSPATH=$CLASSPATH:/(where your java is installed)/bin
To check whether the PATH and CLASSPATH are set correctly, execute
echo $PATH
echo $CLASSPATH
The only issue with this approach is that you have to set it everytime. To avoid this, add these statements to a script and call the script when you start your system.

---

### Post by ju2wheels on 2009-03-05
> **anyone2009 said:**
> thank's alot 


where is the Jdk ?


The jdk is installed in /usr/lib/jvm/java-6-sun but that is not really helpful information to know. 

To use the javac compiler from the jdk just do the following:

```

javac yourClass.java

```

---

### Post by anyone2009 on 2009-03-05
hi,

when i do this 
pdate-java-alternatives -s java-6-sun
it's work 

thank you ju2wheels
and thank to all of you

---

