---
title: "Moneydance won't launch"
date: 2009-10-11
forum: Desktop Environments
---

### Post by hops on 2009-10-11
Problem: Moneydance not starting since last ubuntu update.

When run in a terminal window, I get the following output.  Note that the jvm, /opt/moneydance/jre, is the jvm installed with Moneydance.  There have been no changes to moneydance with the exception of the data file.

	ron@apollo:~$ /opt/moneydance/Moneydance
	testing JVM in /opt/moneydance/jre ...
	testing JVM in /opt/moneydance/jre ...
	testing JVM in /usr ...
	No suitable Java Virtual Machine could be found on your system.
	The version of the JVM must be at least 1.4.
	Please define INSTALL4J_JAVA_HOME to point to a suitable JVM.
	You can also try to delete the JVM cache file /home/ron/.install4j
	ron@apollo:~$ 
	
I followed the instructions to delete the JVM cache file and define INSTALL4j_JAVA_HOME (I set it to /opt/moneydance/jre).  No change.

I haven't written shell in over 10 years, but it looks to me as if the Moneydance script is trying to verify the version number by executing "java -version".  This command, however is returning the string "Error: no `server' JVM at `/opt/moneydance/jre/lib/i386/server/libjvm.so'." rather than the java version number.  

I pointed to a different jvm and everything began to work.  I have no idea as to what changed and I really can't tell from the dates.

I am running ubuntu 9.04.

---

