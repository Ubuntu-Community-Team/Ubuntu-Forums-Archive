---
title: "Thunderbird &quot;Synching Thunder&quot;"
date: 2006-08-04
forum: Desktop Environments
---

### Post by walmartshopper67 on 2006-08-04
I have a desktop and laptop both running Dapper. I need to synchronize my email accounts on both of them, and I am using Thunderbird. I've found a program to do it - but I'm not quite sure how to set it up. Here is the program: [http://synchingthunder.sourceforge.net/]("http://synchingthunder.sourceforge.net/")
, and here are the install directions: [http://synchingthunder.sourceforge.net/install.htm]("http://synchingthunder.sourceforge.net/install.htm")

here is what I'm having trouble with: "And extract all of the files to a directory of your choice. Add these files to your system CLASSPATH variable (adding the directory is not enough, you need to add the individual files)."

I have Java installed (the command 'which java' returns /usr/bin/java), however if I run 'echo $CLASSPATH' it returns nothing. What/how should I set the classpath so it's permanant with the synching thunder stuff in the right place? I know I could run 'export', but that's temporary right? thanks;)

---

### Post by galileon on 2007-03-12
<quote>If you have no idea what a system variable is, then extract them to the 'ext' directory of your JAVA installation (typically /usr/java/jre1.5.0/lib/ext on a linux machine).
</quote>

i did just that, although i havent tested the program yet...

btw my ext path is 
 /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/lib/ext

might be different for you...

to run it,
java net.ivanovic.synchingthunder.SynchingThunderUI -Xmx512M

ask if you need more help...

---

