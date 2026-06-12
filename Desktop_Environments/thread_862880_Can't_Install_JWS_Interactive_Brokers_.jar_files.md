---
title: "Can't Install JWS Interactive Brokers .jar files"
date: 2008-07-17
forum: Desktop Environments
---

### Post by scottyf11 on 2008-07-17
I have a brand new ubuntu 8.04 system with all updates.  I have java 6 runtime installed and libpgjava. I was able to download and extract the java files.  However, I have tried to install the files using ```
java -cp jts.jar;pluginsupport.jar;jcommon-1.0.0.jar;jfreechart-1.0.0.jar;jhall.jar;other.jar;riskfeed.jar;rss.jar -Xmx256M jclient.LoginFrame 
``` format and 

```
java -cp jts.jar;pluginsupport.jar;jcommon-1.0.0.jar;jfreechart-1.0.0.jar;jhall.jar;other.jar:riskfeed.jar;rss.jar -Xmx256M jclient.LoginFrame 
``` format.  both options produced the same errors, 
bash: pluginsupport.jar: command not found
bash: jcommon-1.0.0.jar: command not found
bash: jfreechart-1.0.0.jar: command not found
bash: jhall.jar:other.jar: command not found
bash: riskfeed.jar: command not found
bash: rss.jar: command not found

I've also tried to double click the .jar files, however, it opens them like an archive instead of executing them (I've right clicked each file to enable execution)

---

### Post by tinny on 2008-07-18
Do you know which one of these jar files has the main class?

You can find out by opening each jar file (jars are just zip files) and looking in the META-INF/MANIFEST.MF file for a "Main-Class:" attribute.

Then once you have found this (say it was in "something.jar") you can run it as follows...

```

java -jar something.jar

```

Make sure all the other dependency jars are on the class path (E.g in the same folder will work)

OR...

The easy way to do this (If you have Sun Java installed correctly)

Download this file and start it with Java Web Start.

[www.interactivebrokers.com/en/control/jnlptws.php?file=tws.jnlp](www.interactivebrokers.com/en/control/jnlptws.php?file=tws.jnlp)
Hope this helps.

---

