---
title: "Running an Executable"
date: 2006-07-19
forum: Desktop Environments
---

### Post by macogw on 2006-07-19
ok I have this Genealogy program that I want to run.  It has 4 files that can run it.  They are run.bat, run.sh, and run.cmd. The .cmd and .bat files say:
javaw -Xmx512m -Xms32m -jar run.jar

The .sh file is longer:
```

#!/bin/sh

#GenJ has to be run from inside it's installation directory
#so change into directory where this script was started
cd 'dirname $0'

#check the script for being a symbolik link we can follow
SCRIPT='basename $0'
while [ -h "$SCRIPT" ]; do
 SCRIPT='ls -l $SCRIPT | grep -o '[/.[:alnum:]]*$''
 echo "*** INFO: Following symlink $SCRIPT"
 cd 'dirname $SCRIPT'
 SCRIPT='basename $SCRIPT'
done

#final check if the GenJ main archive is right here
if [ ! -f "./run.jar" ]; then
 echo "*** ERROR: Missing GenJ resource(s) in "'pwd'
 exit 1
fi

#find java
JAVA=$JAVA_HOME/bin/java
if [ ! -x "$JAVA" ]; then
 JAVA='which java'
 if [ $? -eq 1 ]; then
  echo "*** ERROR: Can't find java executable"
  exit 1
 fi
fi

#run it (we start the virtual machine with initially 32 MB 
#and allocate a max of 512 MB)
CMD="$JAVA -Xmx512m -Xms32m -jar run.jar"

echo "*** INFO: Executing '$CMD'"

$CMD

```

I tried to run the .sh file and it told me:
*** INFO Running GenJ from/home/mack/GenJ
*** Executing 'usr/bin/java -Xmx512m -Xms32m -jar run.jar'

And then the program doesn't load up.  It works in Windows, and it's supposed to work in Linux (I got it from sourceforge.net).  Usually in Windows the command prompt appears for a moment then disappears and the GUI comes up.  There's no GUI happening.

[http://genj.sourceforge.net/](http://genj.sourceforge.net/) < there's the program, by the way

---

### Post by svaucher on 2006-07-19
1/  *** Executing 'usr/bin/java -Xmx512m -Xms32m -jar run.jar'

is incorrect because it's missing the initial '/':

usr/bin/java  -> /usr/bin/java

2/ The script is longer than the win .bat since it tries to find your java installation.

try using the default java installation from a terminal:
$ java -jar run.jar

if that works, add the memory parameters (-Xms is min memory, -Xmx is max memory):

For the script to work, you should be able to set an environment variable JAVA_HOME to where your java distribution is stored.

In my environment where I've installed sun's virtual machine:

$ echo $JAVA_HOME
/usr/lib/j2sdk1.5-sun/

The script works like a charm

HTH,
Stephane

---

### Post by reclusivemonkey on 2006-07-19
Bit off topic, but have you looked at gramps? Its in the repos...

[http://gramps-project.org/](http://gramps-project.org/)

---

