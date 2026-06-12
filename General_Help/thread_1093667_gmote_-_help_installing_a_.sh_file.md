---
title: "gmote - help installing a .sh file"
date: 2009-03-11
forum: General Help
---

### Post by phantomjoker on 2009-03-11
Hi there, I have just downloaded the tar.gz file for gmote (server software to allow you to use a g1 mobile to control your computer), and have extracted the file, but now am stuck!

The extracted file leaves me with a .sh file, a .sh~ file, and 2 folders called 'Lib' and 'Bin'.

Apparently I have to install this software before my phone will connect with the computer (...makes sense...) but i don't know what to do, and the website gives no help for linux users. 
[www.gmote.org]("www.gmote.org")
[or at least none i have found]

any help would be great. Thanks


UPDATE - This has turned into more of a JAVA issue (my java not working), please read on...

---

### Post by phantomjoker on 2009-03-11
I used a bit of common sense and ran the script through the terminal, but got this error -

> Starting GmoteServer 2.0 ... 
GmoteServer started.
mckenzie@mckenzie-home:~$ Exception in thread "main" java.lang.NoClassDefFoundError: org/gmote/server/GmoteServerUiLinux
Caused by: java.lang.ClassNotFoundException: org.gmote.server.GmoteServerUiLinux
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268 )
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
Could not find the main class: org.gmote.server.GmoteServerUiLinux. Program will exit.


any ideas?

---

### Post by taurus on 2009-03-11
Could there be a problem with java?  Which version are you using on your machine?

```
java -version
```

---

### Post by phantomjoker on 2009-03-12
I get 

> java version "1.6.0_0"
IcedTea6 1.3.1 (6b12-0ubuntu6.1) Runtime Environment (build 1.6.0_0-b12)
OpenJDK Server VM (build 1.6.0_0-b12, mixed mode)


thanks so far

---

### Post by binbash on 2009-03-12
install sun's java (sun-java6-* )

---

### Post by phantomjoker on 2009-03-12
i already have

sun-java6-bin

sun-java6-jre

sun-java6-plugin

do i need them all (...demo, fonts, doc, javadb, jdk, source?)

cheers

---

### Post by Neo_The_User on 2009-03-12
might need jdk.

---

### Post by phantomjoker on 2009-03-12
i tried to download them all - but when it came to the jdk - it told me i needed to download an archive from a website?! does this sound right? and the synaptic install failed...

---

### Post by taurus on 2009-03-12
What's the output of this command from a terminal?

```
sudo update-alternatives --config java
```

---

### Post by phantomjoker on 2009-03-13
lets see - 

i get the following message -

> There are 5 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/lib/jvm/java-6-sun/jre/bin/java
          2    /usr/bin/gij-4.2
          3    /usr/bin/gij-4.3
          4    /usr/lib/jvm/java-gcj/jre/bin/java
*+        5    /usr/lib/jvm/java-6-openjdk/jre/bin/java

Press enter to keep the default[*], or type selection number: 



does this mean anything? 

cheers

---

### Post by taurus on 2009-03-13
Pick **1** as your default..  Then make sure it is by running this command from a terminal again.

```
java -version
```

---

### Post by phantomjoker on 2009-03-13
Ok, i followed your instructions and the output was the following -

> mckenzie@mckenzie-home:~$ sudo update-alternatives --config java
[sudo] password for mckenzie: 

There are 5 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/lib/jvm/java-6-sun/jre/bin/java
          2    /usr/bin/gij-4.2
          3    /usr/bin/gij-4.3
          4    /usr/lib/jvm/java-gcj/jre/bin/java
*+        5    /usr/lib/jvm/java-6-openjdk/jre/bin/java

Press enter to keep the default[*], or type selection number: 1
Using '/usr/lib/jvm/java-6-sun/jre/bin/java' to provide 'java'.
mckenzie@mckenzie-home:~$ java -version
java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) Server VM (build 11.0-b15, mixed mode)


---

### Post by phantomjoker on 2009-03-13
But again i get the following message

> mckenzie@mckenzie-home:~$ Exception in thread "main" java.lang.NoClassDefFoundError: org/gmote/server/GmoteServerUiLinux
Caused by: java.lang.ClassNotFoundException: org.gmote.server.GmoteServerUiLinux
	at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
Could not find the main class: org.gmote.server.GmoteServerUiLinux.  Program will exit.



---

### Post by phantomjoker on 2009-03-13
interestingly - when i change the default to number 3 i get this

>  sudo update-alternatives --config java
[sudo] password for mckenzie: 

There are 5 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*         1    /usr/lib/jvm/java-6-sun/jre/bin/java
          2    /usr/bin/gij-4.2
          3    /usr/bin/gij-4.3
          4    /usr/lib/jvm/java-gcj/jre/bin/java
 +        5    /usr/lib/jvm/java-6-openjdk/jre/bin/java

Press enter to keep the default[*], or type selection number: 3
Using '/usr/bin/gij-4.3' to provide 'java'.



mckenzie@mckenzie-home:~$ /home/mckenzie/GmoteServerLinux2.0.0/GmoteServer.sh
Starting GmoteServer 2.0 ... 
GmoteServer started.
mckenzie@mckenzie-home:~$ Exception in thread "main" java.lang.NoClassDefFoundError: org.gmote.server.GmoteServerUiLinux
   at gnu.java.lang.MainThread.run(libgcj.so.90)
Caused by: java.lang.ClassNotFoundException: org.gmote.server.GmoteServerUiLinux not found in gnu.gcj.runtime.SystemClassLoader{urls=[], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.90)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.90)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at gnu.java.lang.MainThread.run(libgcj.so.90)

mckenzie@mckenzie-home:~$ 



a slightly different error... (i also get the same message using 4 as default)

---

### Post by phantomjoker on 2009-03-13
I tried reinstalling my java and got the following error

> E: sun-java6-doc: subprocess post-installation script returned error exit status 1

i think this is because it asked me to download some documentation for java, give it root access and place it in my /tmp folder, which i failed to do... but im not sure.

---

### Post by phantomjoker on 2009-03-17
any more help?

---

### Post by riktking on 2009-03-18
hi

hope one of you can help me. i want to run Gmote at startup. it is all installed an i can run it from the terminal, but i want it to run when i log in. im running 8.10, gnome start up. i have tried to follow peoples instructions, but can some one PLEASE help me, im going spare!!

thanks in advance

riktking

---

### Post by Remanifest on 2009-03-22
> **riktking said:**
> hi

hope one of you can help me. i want to run Gmote at startup. it is all installed an i can run it from the terminal, but i want it to run when i log in. im running 8.10, gnome start up. i have tried to follow peoples instructions, but can some one PLEASE help me, im going spare!!

thanks in advance

riktking

It's a bit clunky, but I came up with a solution.  For it to work properly, Gmote Server requires that you be inside of its directory when you start it.

If you haven't done so already, move the Gmote Server folder to ~/.gmote or something similar, so it stays out of your way.

Next, we'll create a file using nano.

```
nano gmote
```
Once nano is open, insert the following, being sure to change the path to where Gmote lives:
```
#!/bin/sh
cd /home/USER/.gmote && ./GmoteServer.sh
```

Next, we'll make it executable and move it to /usr/bin
```
chmod +x ./gmote
sudo mv ./gmote /usr/bin/gmote
```

On the Gnome menu, go to System>Preferences>Sessions and click Add.  Name it whatever you want, and under command, put "/usr/bin/gmote" (without quotes).  Save it, and you're done.

---

### Post by demlasjr on 2009-03-22
i had the same problem trying to install a ups monitoring software, but I resolved uninstalling sun-java6-bin from synaptic package manager and then reinstall.
you need to choose "Mark for complete removal"

---

### Post by bone2006 on 2009-03-30
I am trying to just get it to run.  I used firestarter to open up the ports, I extracted and ran the file in the directory and it comes up and says that it's getting packets from the gphone, but still having problems as I can't access it.

The gphone lets me see it and try to connect to it, but it always says connection problem.

I have another system that has windows and I disabled the firewall and change the IP in my router and instantly I'm having it running.  

Any help getting it with Linux

---

### Post by Remanifest on 2009-04-07
> **bone2006 said:**
> I am trying to just get it to run.  I used firestarter to open up the ports, I extracted and ran the file in the directory and it comes up and says that it's getting packets from the gphone, but still having problems as I can't access it.

The gphone lets me see it and try to connect to it, but it always says connection problem.

I have another system that has windows and I disabled the firewall and change the IP in my router and instantly I'm having it running.  

Any help getting it with Linux

I don't have any experience with the Windows version, but the Linux version must be run from within the directory that Gmote is in.  If it's in $HOME, you must run Gmote from $HOME... /path/to/Gmote will not work.

---

### Post by Remanifest on 2009-04-14
In order for Gmote Server to work, you need to have Sun's Java 6 installed.
```
sudo aptitude install sun-java6-bin sun-java6-jdk sun-java6-jre
```

Next, you'll need to set this up as your default Java Virtual Machine (JVM)
```
sudo update-java-alternatives -s java-6-sun
```

Once you've done that, you shouldn't have any issues with getting this up and running.

---

### Post by Captain_Falafel on 2009-06-05
None of that works for me.. I'm running Jaunty.. and when I cd topathoffile and run GmoteServer.sh in the terminal, I get 'command not found':

```
:~/Desktop/GmoteServerLinux2.0.0$ GmoteServer.sh
bash: GmoteServer.sh: command not found

```

---

### Post by zelluloidtraum on 2009-07-02
Is it necessary for you to run this in a terminal? 

I was running into the same problem so I gave up and ran it from Graphical instead. Just click the Gmoteserver.sh and chose the "Run" option.

I know that's an unacceptable answer for some people....just throwing it out there.

---

### Post by Captain_Falafel on 2009-07-05
> **zelluloidtraum said:**
> Is it necessary for you to run this in a terminal? 

I was running into the same problem so I gave up and ran it from Graphical instead. Just click the Gmoteserver.sh and chose the "Run" option.

I know that's an unacceptable answer for some people....just throwing it out there.

hahahaha.. lmao IT WORKS!
who would've thought it to be that easy? :popcorn:

thanks zelluloidtraum :p
ohhh the laziness this will bring

---

### Post by Remanifest on 2009-08-02
The file must be executable to run it directly from command line (chmod +x), or you can run it "with "sh ./file.sh" - this was all stated in my previous post.

---

### Post by thiefy on 2009-10-07
that worked for me too. thank you. just right click on the file in nautilus and select run you don't need to mess with this java junk. your right, it brings laziness and we aren't learning what is really going on, but 'we' don't have time for that. thanks for the great answer zelluloidtraum

---

### Post by 1awesomeguy on 2009-11-12
The following will work if you cd into the correct folder

```
sh GmoteServer.sh
```

---

### Post by optimal on 2010-04-11
@Remanifest - Cheers fella, your little script worked a treat - looks like it's working dandy for me - legendary!

---

### Post by JoeGoalie on 2010-06-13
Edit: Nevermind, I had messed up a step when following post#18.  Now it is working perfectly!  Thank you Remanifest.

---

### Post by nix.ward on 2011-01-02
I'm running 10.10 and found I had to add a 'sleep' delay in the gmote script:

```
#!/bin/sh
sleep 10
cd /home/USER/.gmote && ./GmoteServer.sh
```

If I didn't do this the gmote server would not respond to gmote client commands and the JVM would start chewing up a lot of CPU cycles after freshly booting the machine.  Unfortunately I don't really have an explanation to why this was happening but the sleep delay seemed to help.  If anyone has an explanation I would really appreciate it.  Thanks.

> **Remanifest said:**
> It's a bit clunky, but I came up with a solution.  For it to work properly, Gmote Server requires that you be inside of its directory when you start it.

If you haven't done so already, move the Gmote Server folder to ~/.gmote or something similar, so it stays out of your way.

Next, we'll create a file using nano.

```
nano gmote
```
Once nano is open, insert the following, being sure to change the path to where Gmote lives:
```
#!/bin/sh
cd /home/USER/.gmote && ./GmoteServer.sh
```

Next, we'll make it executable and move it to /usr/bin
```
chmod +x ./gmote
sudo mv ./gmote /usr/bin/gmote
```

On the Gnome menu, go to System>Preferences>Sessions and click Add.  Name it whatever you want, and under command, put "/usr/bin/gmote" (without quotes).  Save it, and you're done.

---

### Post by kashifmehmood on 2011-01-29
Thank you very much. Problem solved for me..

---

### Post by SnoopFogg on 2011-04-22
> **Remanifest said:**
> It's a bit clunky, but I came up with a solution.  For it to work properly, Gmote Server requires that you be inside of its directory when you start it.

If you haven't done so already, move the Gmote Server folder to ~/.gmote or something similar, so it stays out of your way.

Next, we'll create a file using nano.

```
nano gmote
```
Once nano is open, insert the following, being sure to change the path to where Gmote lives:
```
#!/bin/sh
cd /home/USER/.gmote && ./GmoteServer.sh
```

Next, we'll make it executable and move it to /usr/bin
```
chmod +x ./gmote
sudo mv ./gmote /usr/bin/gmote
```

On the Gnome menu, go to System>Preferences>Sessions and click Add.  Name it whatever you want, and under command, put "/usr/bin/gmote" (without quotes).  Save it, and you're done.

Hi, I'm really struggling with this.  Having followed these instructions I can now launch by:

russ@russ-desktop:~$ cd /usr/bin/gmote
russ@russ-desktop:/usr/bin/gmote$ sh GmoteLaunch.sh

But Gmote still doesn't launch on startup.  I used Gedit rather than nano - what should I call that file?  And where should it be saved?  Any help much appreciated

---

### Post by arrimapirate on 2011-07-02
Im sttill having the same error as the op. I updated java set sun java to be the default and still get the same error

Edit: i get this error when attempting to play a song 
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xb770b3a0, pid=2852, tid=2346515312
#
# JRE version: 6.0_24-b07
# Java VM: Java HotSpot(TM) Server VM (19.1-b02 mixed mode linux-x86 )
# Problematic frame:
# C  [libc.so.6+0xcd3a0]  tfind+0x20
#
# An error report file with more information is saved as:
# /home/xbmc/Desktop/GmoteServerLinux2.0.0/hs_err_pid2852.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#

---

### Post by ingo on 2012-02-29
Am getting similar error with openjdk7. Have tried all  approaches in this thread bar installing Oracle's java (in which case it probably would work...). 

> #
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGBUS (0x7) at pc=0x00007f31d102d7f8, pid=20267, tid=139850575496960
#
# JRE version: 7.0_03-b147
# Java VM: OpenJDK 64-Bit Server VM (22.0-b10 mixed mode linux-amd64 compressed oops)
# Derivative: IcedTea7 2.1
# Distribution: Custom build (Wed Feb 15 14:16:08 UTC 2012)
# Problematic frame:
# C  [libc.so.6+0xe07f8]  tfind+0x18
#
# Failed to write core dump. Core dumps have been disabled. To enable core dumping, try "ulimit -c unlimited" before starting Java again
#
# An error report file with more information is saved as:
# /home/toad/.gmote/hs_err_pid20267.log
#
# If you would like to submit a bug report, please include
# instructions on how to reproduce the bug and visit:
#   [http://icedtea.classpath.org/bugzilla](http://icedtea.classpath.org/bugzilla)
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#
Also, the steps in post #18 don't make a lot of sense to me. 
> If you haven't done so already, move the Gmote Server folder to ~/.gmote or something similar, so it stays out of your way.

Next, we'll create a file using nano.


nano gmote
Once nano is open, insert the following, being sure to change the path to where Gmote lives:

#!/bin/sh
cd /home/USER/.gmote && ./GmoteServer.sh

Next, we'll make it executable and move it to /usr/bin

chmod +x ./gmote
sudo mv ./gmote /usr/bin/gmoteIn which directory is the file gmote and in the example above are we not attempting to move the entire ~/.gmote folder to /usr/bin?

---

### Post by hungry_pete on 2012-04-05
> **Remanifest said:**
> It's a bit clunky, but I came up with a solution.  For it to work properly, Gmote Server requires that you be inside of its directory when you start it.

If you haven't done so already, move the Gmote Server folder to ~/.gmote or something similar, so it stays out of your way.

Next, we'll create a file using nano.

```
nano gmote
```
Once nano is open, insert the following, being sure to change the path to where Gmote lives:
```
#!/bin/sh
cd /home/USER/.gmote && ./GmoteServer.sh
```

Next, we'll make it executable and move it to /usr/bin
```
chmod +x ./gmote
sudo mv ./gmote /usr/bin/gmote
```

On the Gnome menu, go to System>Preferences>Sessions and click Add.  Name it whatever you want, and under command, put "/usr/bin/gmote" (without quotes).  Save it, and you're done.

Great advice - thanks for the guide. I had a bit of trouble getting it to work. After moving the gmote executable file into the bash directory, I tested it by typing 'gmote' in a terminal and kept getting an error message saying something like "Unable to open file GmoteServer.sh".

I found that I could run GmoteServer.sh with the code:
```
cd /home/USER/.gmote
sh ./GmoteServer.sh
```
This would open the server. So, I adjusted the gmote script to:
```
#!/bin/sh
cd /home/USER/.gmote && sh ./GmoteServer.sh
```
And everything was hunky dorey. It now automatically starts on log in, or I can start it by typing 'gmote' in a terminal. I'm really impressed with this bit of software! Its really satisfying with it hooked up to my media pc in my lounge and I don't have to dig out a bulky keyboard and mouse when doing simple tasks.

My next task is to find a similar thing that will work with an ipad and ubuntu.

---

### Post by effn10 on 2012-10-26
Hi everybody,

I have struggled for a couple of weeks on Gmote and its installation, and now that it runs correctly, I'll share my experience.

I'm running Ubuntu 10.04 and had OpenJDK as a java machine.

I found out that the Sun version of Java worked with Gmote - otherwise I had the java.awt.SystemTray error.

I downloaded [COLOR="Blue"][this version of Java]("http://www.java.com/en/download/help/linux_install.xml")[/COLOR].

I let you follow the instructions there, I will only copy the code extracts - and adapt them to my case/choice
```

sudo cd /usr/java/
sudo tar zxvf jre-7u7-linux-i586.tar.gz

```

Then I found out [COLOR="blue"][here]("http://blog.manishchhabra.com/2012/05/installing-oracle-sun-java-jdk-and-setting-java_home-in-ubuntu-linux/")[/COLOR] that the java machine had to be somehow registered in the system.

```

sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/jdk1.7.0_04/bin/java" 1
sudo update-alternatives --config java

```

As GmoteServer must run in local, I changed the code in GmoteServer.sh: at the beginning of the file, I added the line
```
cd /usr/GmoteServerLinux2.0.0
```

Delay on startup is needed, as said earlier in this thread, and in [COLOR="blue"][that one]("https://groups.google.com/group/gmote-users/tree/browse_frm/month/2010-04/81e42a27f569f199?rnum=11&_done=%2Fgroup%2Fgmote-users%2Fbrowse_frm%2Fmonth%2F2010-04%3F")[/COLOR].
So I created a file GmoteServerStartup.sh as a copy of GmoteServer.sh for the specific needs of the startup.
at the beginning of GmoteServerStartup.sh, I added line
```

sleep 10

```

Then I moved folder GmoteServerLinux2.0.0 to /usr/
```
sudo mv GmoteServerLinux2.0.0 /usr/GmoteServerLinux2.0.0
```

To create shortcuts in the Main Menu and the Startup Applications list, I created links in /usr/bin
```

sudo cp -l /usr/GmoteServerLinux2.0.0/GmoteServer.sh /usr/bin/GmoteServer
sudo cp -l /usr/GmoteServerLinux2.0.0/GmoteServerStartup.sh /usr/bin/GmoteServerStartup

```

Then I added GmoteServer to the Main Menu, in Sound & Video, and added GmoteServerStartup to the Startup Applications with comment: Starts Gmote after a short delay to allow Java to start.

In case of problem of permission for GmoteServerStartup, you have to change the ownership of the file (replace <user> by your user login)
```
sudo chown <user> /usr/GmoteServerLinux2.0.0/GmoteServerStartup.sh
```

That's all I know! Hope it helps...

---

