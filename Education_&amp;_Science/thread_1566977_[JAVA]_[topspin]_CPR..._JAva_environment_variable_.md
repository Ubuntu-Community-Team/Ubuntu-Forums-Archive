---
title: "[JAVA] [topspin] CPR:... JAva environment variable not set"
date: 2010-09-03
forum: Education &amp; Science
---

### Post by inaho on 2010-09-03
dear all,
I am desperately trying to install TOPSPIN (not the tennis game, a NMR software...) on ubuntu 10.4

it worked on ubuntu 8.04 but I guess I am now facing a problem with JAVA, since all the installation procedures seems to work fine until I try to run the program and I got this:

> /opt/topspin/topspin: 366: source: not found
CPR : Path to prog : "/opt/topspin/prog"
CPR : Path to exp  : "/opt/topspin/exp"
CPR : Path to conf : "/opt/topspin/conf"
CPR : waiting for FLEXlm license
CPR : FLEXlm license is valid until 2011-04-06
CPR : 2010-09-03 10:21:37.866 +0200 environment variable JAVA not set
Program is exiting ...

Hit ENTER to continue ... 

so, I went to the folder /opt/topspin and I tried to modify the javaenv.sh file:

previous (this is only end of the file):
> #****************************************************************
# These variables are used to start the JAVA client.
#****************************************************************
export JAVA=$XWINNMRHOME/jre/bin/java
export JAVA_ARGS="$SPLASH_OPTIONS $MEMORY $CP $GRAPHICS_OPTIONS $VERIFY $SYSTEM_PROPS -jar ./classes/lib/topspin.jar" 

my (unsuccessful) modifications:
> #****************************************************************
# These variables are used to start the JAVA client.
#****************************************************************

#export JAVA=$XWINNMRHOME/usr/bin/java
export JAVA=$XWINNMRHOME/usr/lib/jvm/java-6-sun

export JAVA_ARGS="$SPLASH_OPTIONS $MEMORY $CP $GRAPHICS_OPTIONS $VERIFY $SYSTEM_PROPS -jar ./classes/lib/topspin.jar"

I modifyed also the file (in my home) .bash.rsc with these lines:

> #JAVA_HOME added by barbara
export JAVA_HOME=/usr/lib/jvm/java-6-sun

and if I ask whereis java I got
java: /usr/bin/java /usr/lib/java /usr/share/java /usr/share/man/man1/java.1.gz


do you have some suggestions?

:S

---

### Post by inaho on 2010-09-06
ok, I found the solution...

it is included in the topspin installation procedure on this post:

[http://ubuntuforums.org/showthread.php?p=9813416#post9813416](http://ubuntuforums.org/showthread.php?p=9813416#post9813416)

---

