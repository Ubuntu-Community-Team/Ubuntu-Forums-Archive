---
title: "Installing Sun's Java without using Repositories"
date: 2009-06-08
forum: General Help
---

### Post by eyeprotocol on 2009-06-08
Hello all

In the past i have been installing Sun's Java by extracting the bin file into a directory and setting JAVA_HOME and PATH properly. I did the same thing with Ubuntu 9.04.

These are the final two lines of my /etc/profile:
```
export JAVA_HOME=/usr/local/java/jdk1.6.0-14
export PATH=$PATH:/usr/local/java/jdk1.6.0-14/bin
```


So, my JAVA_HOME and PATH is as follows:

```
echo $JAVA_HOME
/usr/local/java/jdk1.6.0-14
```

```
echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

Also, i tried to install the firefox java plugin, as follows:
```
ln -s /usr/local/java/jdk1.6.0_14/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins/
```

There are two problems:

a) First, typing "javac" and pressing <enter> results in this:
```
The program 'javac' can be found in the following packages:
 * openjdk-6-jdk
 * ecj
 * gcj-4.3
 * java-gcj-compat-dev
 * gcj-4.2
 * jikes-classpath
 * jikes-kaffe
 * kaffe
 * sun-java5-jdk
 * sun-java6-jdk
Try: apt-get install <selected package>
```

... which is obviously not what i want.

b) The firefox plugin is not working.

So, here are the questions:
*How do i get rid of Ubuntu's thoughts that i might wish to install one of its own packages or running Java. How do i get the firefox plugin to work?*

Please assist.

Panos

---

### Post by Legace on 2009-06-08
Follow this tuto:
[http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/](http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/)

---

