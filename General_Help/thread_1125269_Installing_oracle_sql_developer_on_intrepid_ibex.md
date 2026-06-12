---
title: "Installing oracle sql developer on intrepid ibex"
date: 2009-04-14
forum: General Help
---

### Post by Exile09 on 2009-04-14
Can some please tell me how to install oracle sql developer under ubuntu 8.10?

I've tryed various things on the web with no luck, and I really dont want to install a copy of windows xp just for this app!

---

### Post by ju2wheels on 2009-04-14
Which part are you stuck on? The isntructions are right under the download link here: [http://www.oracle.com/technology/software/products/sql/index.html](http://www.oracle.com/technology/software/products/sql/index.html) You will want to download the last one listed there, not the RPM.

---

### Post by Exile09 on 2009-04-16
I've installed sql developer & it keeps asking be for a java executable which I cant find!

I have the JDK installed so I know its on the machine somewhere!

---

### Post by ju2wheels on 2009-04-16
Run the following in the terminal:

```

sudo update-java-alternatives -s java-6-sun

```

Remember that your system may also have OpenJDK installed and it is most likely configured as the system's default Java virtual machine in which case it will take precedence over Sun's version of Java. You will most likely need to install Sun's version and make it the default using the above command.

---

### Post by Exile09 on 2009-04-16
Thanks for your help! it is much appreciated!

Ok after running that I get:

```
Using '/usr/lib/jvm/java-6-sun/bin/appletviewer' to provide 'appletviewer'.
Using '/usr/lib/jvm/java-6-sun/bin/apt' to provide 'apt'.
Using '/usr/lib/jvm/java-6-sun/bin/extcheck' to provide 'extcheck'.
Using '/usr/lib/jvm/java-6-sun/bin/HtmlConverter' to provide 'HtmlConverter'.
Using '/usr/lib/jvm/java-6-sun/bin/idlj' to provide 'idlj'.
Using '/usr/lib/jvm/java-6-sun/bin/jarsigner' to provide 'jarsigner'.
Using '/usr/lib/jvm/java-6-sun/bin/jar' to provide 'jar'.
Using '/usr/lib/jvm/java-6-sun/bin/javac' to provide 'javac'.
Using '/usr/lib/jvm/java-6-sun/bin/javadoc' to provide 'javadoc'.
Using '/usr/lib/jvm/java-6-sun/bin/javah' to provide 'javah'.
Using '/usr/lib/jvm/java-6-sun/bin/javap' to provide 'javap'.
Using '/usr/lib/jvm/java-6-sun/bin/java-rmi.cgi' to provide 'java-rmi.cgi'.
Using '/usr/lib/jvm/java-6-sun/bin/jconsole' to provide 'jconsole'.
Using '/usr/lib/jvm/java-6-sun/bin/jdb' to provide 'jdb'.
Using '/usr/lib/jvm/java-6-sun/bin/jhat' to provide 'jhat'.
Using '/usr/lib/jvm/java-6-sun/bin/jinfo' to provide 'jinfo'.
Using '/usr/lib/jvm/java-6-sun/bin/jmap' to provide 'jmap'.
Using '/usr/lib/jvm/java-6-sun/bin/jps' to provide 'jps'.
Using '/usr/lib/jvm/java-6-sun/bin/jrunscript' to provide 'jrunscript'.
Using '/usr/lib/jvm/java-6-sun/bin/jsadebugd' to provide 'jsadebugd'.
Using '/usr/lib/jvm/java-6-sun/bin/jstack' to provide 'jstack'.
Using '/usr/lib/jvm/java-6-sun/bin/jstatd' to provide 'jstatd'.
Using '/usr/lib/jvm/java-6-sun/bin/jstat' to provide 'jstat'.
Using '/usr/lib/jvm/java-6-sun/bin/native2ascii' to provide 'native2ascii'.
Using '/usr/lib/jvm/java-6-sun/bin/rmic' to provide 'rmic'.
Using '/usr/lib/jvm/java-6-sun/bin/schemagen' to provide 'schemagen'.
Using '/usr/lib/jvm/java-6-sun/bin/serialver' to provide 'serialver'.
Using '/usr/lib/jvm/java-6-sun/bin/wsgen' to provide 'wsgen'.
Using '/usr/lib/jvm/java-6-sun/bin/wsimport' to provide 'wsimport'.
Using '/usr/lib/jvm/java-6-sun/bin/xjc' to provide 'xjc'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/ControlPanel' to provide 'ControlPanel'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/java' to provide 'java'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/java_vm' to provide 'java_vm'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/javaws' to provide 'javaws'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/jcontrol' to provide 'jcontrol'.
Using '/usr/lib/jvm/java-6-sun/jre/lib/jexec' to provide 'jexec'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/keytool' to provide 'keytool'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/orbd' to provide 'orbd'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/pack200' to provide 'pack200'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/policytool' to provide 'policytool'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/rmid' to provide 'rmid'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/rmiregistry' to provide 'rmiregistry'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/servertool' to provide 'servertool'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/tnameserv' to provide 'tnameserv'.
Using '/usr/lib/jvm/java-6-sun/jre/bin/unpack200' to provide 'unpack200'.
Using '/usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so' to provide 'firefox-javaplugin.so'.
Using '/usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so' to provide 'iceape-javaplugin.so'.
Using '/usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so' to provide 'iceweasel-javaplugin.so'.
Using '/usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so' to provide 'midbrowser-javaplugin.so'.
Using '/usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so' to provide 'mozilla-javaplugin.so'.
Using '/usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so' to provide 'xulrunner-1.9-javaplugin.so'.
Using '/usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so' to provide 'xulrunner-javaplugin.so'.

``` 

Which suggests to me that it is installed, but I may be wrong as I'm still a newbie when it comes to Linux!

---

### Post by ju2wheels on 2009-04-16
Yes that is correct output. Is Oracle still having problems? If you could provide a more precise error message it would be easier to pinpoint the problem.

---

### Post by Exile09 on 2009-04-16
I'm not having an error as such, Basically I open up sql developer and I get this:
[[IMG]http://s2.largeimagehost.com/TN/ehrrhsh/tn_ss.jpg[/IMG]](http://s2.largeimagehost.com/img/untilted/ehrrhsr/ss.jpg.html)
(click to enlarge)

I also don't know the path for the 'java executable'

---

### Post by ju2wheels on 2009-04-16
According to this: [http://forums.oracle.com/forums/thread.jspa?threadID=584131](http://forums.oracle.com/forums/thread.jspa?threadID=584131) there is a sqldeveloper.conf file somewhere.

Try running the following command:
```

sudo find / -name "*sqldeveloper.conf"

```

Look for a line where it sets the java path and replace it with this path:
```

/usr/lib/jvm/java-6-sun/bin

```

If its not in the file then set it yourself by adding the following line to the file as the above thread sugggests:
```

SetJavaHome /usr/lib/jvm/java-6-sun/bin

```

---

### Post by ju2wheels on 2009-04-16
> **Exile09 said:**
> I'm not having an error as such, Basically I open up sql developer and I get this:
[[IMG]http://s2.largeimagehost.com/TN/ehrrhsh/tn_ss.jpg[/IMG]](http://s2.largeimagehost.com/img/untilted/ehrrhsr/ss.jpg.html)
(click to enlarge)

I also don't know the path for the 'java executable'

Thats weird, did you use the Windows version of the installer and run it using Wine? Linux doesnt have .exe executables so its weird that it would ask for that specifically... If you did use the windows installer then you will have to install the windows version of Sun Java using wine as well which Im not sure how compatible that will be with Wine.

---

### Post by Exile09 on 2009-04-16
hmm I dont see any line and I've tried adding it manually but I still have the same problem.

After adding the line you suggested my config file looks like:
```
IncludeConfFile ../../ide/bin/ide.conf

AddVMOption  -Dapple.laf.useScreenMenuBar=true 
AddVMOption  -Dcom.apple.mrj.application.apple.menu.about.name="SQL_Developer"
AddVMOption  -Dcom.apple.mrj.application.growbox.intrudes=false 
AddVMOption  -Dcom.apple.macos.smallTabs=true 
AddVMOption  -Doracle.ide.util.AddinPolicyUtils.OVERRIDE_FLAG=true

AddVMOption -Dsun.java2d.ddoffscreen=false

AddVMOption -Dwindows.shell.font.languages=

AddVMOption  -XX:MaxPermSize=128M


IncludeConfFile  sqldeveloper-nondebug.conf

SetJavaHome /usr/lib/jvm/java-6-sun/bin
```

And Once again thank you so much for your help!

---

### Post by Exile09 on 2009-04-16
> **ju2wheels said:**
> Thats weird, did you use the Windows version of the installer and run it using Wine? Linux doesnt have .exe executables so its weird that it would ask for that specifically... If you did use the windows installer then you will have to install the windows version of Sun Java using wine as well which Im not sure how compatible that will be with Wine.

No its defiantly not the windows version via WINE. I installed Oracle SQL Developer for other platforms like you suggested.

I was originally playing around with the .RPM version with alien but I had a similar issue so I figured I give this way a try.......

---

### Post by ju2wheels on 2009-04-16
The other thing to try is to see if it actually does use JAVA_HOME by running this:
```

export JAVA_HOME=/usr/lib/jvm/java-6-sun

```

Then try running it again and see if it works.

---

### Post by Exile09 on 2009-04-16
nope same thing I'm afraid :(

Are you sure its definitely the other platform version I need and not the .rpm linux version?!?

---

### Post by ju2wheels on 2009-04-16
Yep, Ubuntu uses .deb installers and not .rpm, therefore you could use alien to convert the .rpm to .deb but its not guaranteed to work properly so its typically recommended to compile from source at that point or use the alternative installer in this case.

Ive found this as well: [http://mennan.kagitkalem.com/HowToRunOracleSQLDeveloperInUbuntu.aspx](http://mennan.kagitkalem.com/HowToRunOracleSQLDeveloperInUbuntu.aspx)

So try adding it to your path as well:
```

export PATH=$JAVA_HOME/bin:$PATH

```

If that doesnt work Ive also found information that states there is a jdk.conf in the same folder as sqldeveloper.conf (or at least there is on Windows) and if thats also present on the Linux setup then that may also help configure the Java path.

Hope that helps.

---

