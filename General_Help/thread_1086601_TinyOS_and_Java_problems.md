---
title: "TinyOS and Java problems"
date: 2009-03-04
forum: General Help
---

### Post by Ana de Pablo on 2009-03-04
Hi everyone!

I'm working with TinyOS-2.1 and Ubuntu 8.04, but I'm having some problems with Java... I need to create the libmote.a, but when I type 'make', it can't find some of the libraries, and I'm pretty sure that the problem is about the Java path... 

Here is my classpath at the .sh file:

TOSROOT=/opt/tinyos-2.1.0
TOSDIR=$TOSROOT/tos
CLASSPATH=$TOSROOT/support/sdk/java/tinyos.jar:.
MAKERULES=$TOSROOT/support/make/Makerules
LOWPAN_ROOT=$TOSROOT/contrib/berkeley/b6lowpan
TOSMAKE_PATH="$LOWPAN_ROOT/support/make"

But when I try lo locate java:

tos-locate-jre --java
/usr/lib/jvm/java-1.5.0-sun/bin

Should I add another environmental variable (as JAVA_HOME and PATH)?

Any help would be great! Thank you in advance!!!

Ana.

---

