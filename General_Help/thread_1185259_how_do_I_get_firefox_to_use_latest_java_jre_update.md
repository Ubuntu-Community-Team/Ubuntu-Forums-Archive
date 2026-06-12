---
title: "how do I get firefox to use latest java jre update 14 I installed?"
date: 2009-06-12
forum: General Help
---

### Post by Brian_Newbie on 2009-06-12
I just updated my java version to sun java from openJDK java version "1.6.0_0." Before the update my java version showed in terminal as follows: 


brian@brian-laptop:~$ java -version
java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.4.1) (6b14-1.4.1-0ubuntu7)
OpenJDK 64-Bit Server VM (build 14.0-b08, mixed mode)
brian@brian-laptop:~$

Now the same java version command yields the following:

brian@brian-laptop:~$ java -version
java version "1.6.0_14"
Java(TM) SE Runtime Environment (build 1.6.0_14-b08)
Java HotSpot(TM) 64-Bit Server VM (build 14.0-b16, mixed mode)
brian@brian-laptop:~$ 

But when I returned to my Government website that requires sun java 6 update 14 it now tells me I have 1.6.0 update 13 along with the javatester.org website. Update 13 I believe is part of the sun java6 that came with Jaunty Jackalope distro along with OpenJDK.  

I believe the issue is that firefox is not recognizing my newly installed java version 1.6.0_14? 

To install update 14 I followed the scripts on this website: 
[http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/](http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/) 
It installed successfully as indicated with the following terminal output. (I realized it was for hardy but thought the scripts would work with Jaunty). 

brian@brian-laptop:~$ java -version
java version "1.6.0_14"
Java(TM) SE Runtime Environment (build 1.6.0_14-b08)
Java HotSpot(TM) 64-Bit Server VM (build 14.0-b16, mixed mode)

Is the reason firefox is not recognizing update 14 due to an error in the following scripts I used?

To make update 14 the default I used:


brian@brian-laptop:/opt/java/64$ sudo update-alternatives --install "/usr/bin/java" "java" "/opt/java/64/jre1.6.0_14/bin/java" 1
brian@brian-laptop:/opt/java/64$ sudo update-alternatives --set java /opt/java/64/jre1.6.0_14/bin/java
Using '/opt/java/64/jre1.6.0_14/bin/java' to provide 'java'.

Then I attempted to remove icedtea in this fashion and received the following output:

brian@brian-laptop:~$ sudo apt-get remove icedtea-gcjwebplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package icedtea-gcjwebplugin is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

(IcedTea did absolutely show up in firefox's "about:plugins" after that command was ran but now icedtea does not show up there).

Then I attempted to remove any former mozilla plugins for what I thought was version 1.6.0_13 and received this output:


brian@brian-laptop:~$ rm ~/.mozilla/plugins/libnpjp2.so
rm: cannot remove `/home/brian/.mozilla/plugins/libnpjp2.so': No such file or directory
brian@brian-laptop:~$ mkdir ~/.mozilla/plugins
brian@brian-laptop:~$ ln -s /opt/java/64/jre1.6.0_13/lib/amd64/libnpjp2.so ~/.mozilla/plugins/brian@brian-laptop:~$ 

I restarted firefox after I ran those commands. 

Then I noticed I used 13 in that last line and not 14 so I ran that last command again and got the following output:

brian@brian-laptop:~$ ln -s /opt/java/64/jre1.6.0_14/lib/amd64/libnpjp2.so ~/.mozilla/plugins/
ln: creating symbolic link `/home/brian/.mozilla/plugins/libnpjp2.so': File exists
brian@brian-laptop:~$ 

All I want is for jre 1.6.0_13 to show as removed or updated to version 14 and for firefox and websites to recognize the new java version.

How can I get firefox to use jre1.6.0_14?

Thanks

Brian

---

### Post by Brian_Newbie on 2009-06-12
I just thought that I'd try the copy command and received a "dangling symlink" output reply. Just wondering if this has anything to do with firefox not showing latest java jre1.6.0_14?

brian@brian-laptop:~$ cp /opt/java/64/jre1.6.0_14/lib/amd64/libnpjp2.so ~/.mozilla/plugins/
cp: not writing through dangling symlink `/home/brian/.mozilla/plugins/libnpjp2.so'
brian@brian-laptop:~$

---

### Post by Soul-Sing on 2009-06-12
```
sudo update-alternatives --install "/usr/bin/java" "java" "/opt/java/64/jre1.6.0_14/bin/java" 1
sudo update-alternatives --set java /opt/java/64/jre1.6.0_14/bin/java
```

when using /opt/java/64

you can check your steps: [http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/](http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/)

---

### Post by Wayne_V on 2009-06-12
make sure there is no java plugin in /usr/lib/mozilla/plugins (I believe you're OK here since you removed IcedTea)

Then add "-f" to ln to make it overwrite the previous (broken) link:

 ln -sf /opt/java/64/jre1.6.0_14/lib/amd64/libnpjp2.so ~/.mozilla/plugins/

"ls -l ~/.mozilla/plugins" should now show the correct link

---

### Post by Brian_Newbie on 2009-06-12
When I ran command below I received a "libjavaplugin.so" plugin for java. Should this be removed before executing your command: ln -sf /opt/java/64/jre1.6.0_14/lib/amd64/libnpjp2.so ~/.mozilla/plugins/? 

And if I need to remove "libjavaplugin.so" Do I simply use the rm command?  

brian@brian-laptop:~$ sudo ls -1 /usr/lib/mozilla/plugins
[sudo] password for brian: 
flashplugin-alternative.so
libjavaplugin.so
libtotem-cone-plugin.so
libtotem-gmp-plugin.so
libtotem-mully-plugin.so
libtotem-narrowspace-plugin.so
brian@brian-laptop:~$

---

### Post by Wayne_V on 2009-06-12
You can just rm it, yes.  

I would check where it came from:

ls -l (that's ell) /usr/lib/mozilla/plugins
-or-
dpkg --search libjavaplugin.so

---

### Post by Brian_Newbie on 2009-06-12
The libjavaplugin.so appears to have come from etc/alternatives/mozilla-javaplugin.so as follows: 

brian@brian-laptop:~$ ls -l /usr/lib/mozilla/plugins
total 0
lrwxrwxrwx 1 root root 37 2009-04-29 22:33 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
lrwxrwxrwx 1 root root 39 2009-06-05 03:14 libjavaplugin.so -> /etc/alternatives/mozilla-javaplugin.so
lrwxrwxrwx 1 root root 43 2009-04-27 21:59 libtotem-cone-plugin.so -> ../../totem/default/libtotem-cone-plugin.so
lrwxrwxrwx 1 root root 42 2009-04-27 21:59 libtotem-gmp-plugin.so -> ../../totem/default/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root 44 2009-04-27 21:59 libtotem-mully-plugin.so -> ../../totem/default/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root 50 2009-04-27 21:59 libtotem-narrowspace-plugin.so -> ../../totem/default/libtotem-narrowspace-plugin.so
brian@brian-laptop:~$


and the 2nd command does not yield anything

brian@brian-laptop:~$ dpkg --search libjavaplugin.so
dpkg: *libjavaplugin.so* not found.

---

### Post by Brian_Newbie on 2009-06-12
Unless I need to remove the mozilla-javaplugin.so from etc/alternatives/mozilla-javaplugin.so, when I ran the command below it highlighted "/opt/java/64/jre1.6.0_13/lib/amd64/libnpjp2.so" in red letters on a black background (due obviously to the number 13 rather than the latest update 14). 

Would the overwrite command "ln -sf /opt/java/64/jre1.6.0_14/lib/amd64/libnpjp2.so ~/.mozilla/plugins/" work by itself. Or does mozilla-javaplugin.so have to be removed first?

brian@brian-laptop:~$ ls -l ~/.mozilla/plugins
total 0
lrwxrwxrwx 1 brian brian 46 2009-06-12 01:26 libnpjp2.so -> /opt/java/64/jre1.6.0_13/lib/amd64/libnpjp2.so
brian@brian-laptop:~$

Thanks again.

---

### Post by Wayne_V on 2009-06-12
You can drill down further to see where libjava comes from:

 ls -l /etc/alternatives/mozilla-javaplugin.so

I what's in ~/.mozilla/plugins will override /usr/lib/mozilla/plugins but not certain.  Could just as well remove it.

---

