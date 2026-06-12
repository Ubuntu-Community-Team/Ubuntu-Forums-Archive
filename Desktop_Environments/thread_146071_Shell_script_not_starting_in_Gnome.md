---
title: "Shell script not starting in Gnome"
date: 2006-03-17
forum: Desktop Environments
---

### Post by bardu on 2006-03-17
Starting Tomcat's *startup.sh* shell script from the console works fine, but it won't start in Gnome.  After clicking the RUN button nothing happens.  With my previous Linux distribution this was never an issue.

How do I have to configure Gnome (nautilus) to run shell scripts?

Thanks.
Stephan

---

### Post by taurus on 2006-03-17
Just a wild guess but maybe you need to put it in your path!  Also, check to see if the permission is right.  Otherwise, post your script here and someone will see if there is something wrong with it.

---

### Post by bardu on 2006-03-17
Permission is okay and here is the script which ships with Tomcat:
```
#!/bin/sh
# -----------------------------------------------------------------------------
# Start Script for the CATALINA Server
#
# $Id: startup.sh,v 1.4 2004/11/17 20:17:46 yoavs Exp $
# -----------------------------------------------------------------------------

# Better OS/400 detection: see Bugzilla 31132
os400=false
case "`uname`" in
CYGWIN*) cygwin=true;;
OS400*) os400=true;;
esac

# resolve links - $0 may be a softlink
PRG="$0"

while [ -h "$PRG" ] ; do
  ls=`ls -ld "$PRG"`
  link=`expr "$ls" : '.*-> \(.*\)$'`
  if expr "$link" : '.*/.*' > /dev/null; then
    PRG="$link"
  else
    PRG=`dirname "$PRG"`/"$link"
  fi
done
 
PRGDIR=`dirname "$PRG"`
EXECUTABLE=catalina.sh

# Check that target executable exists
if $os400; then
  # -x will Only work on the os400 if the files are: 
  # 1. owned by the user
  # 2. owned by the PRIMARY group of the user
  # this will not work if the user belongs in secondary groups
  eval
else
  if [ ! -x "$PRGDIR"/"$EXECUTABLE" ]; then
    echo "Cannot find $PRGDIR/$EXECUTABLE"
    echo "This file is needed to run this program"
    exit 1
  fi
fi 

exec "$PRGDIR"/"$EXECUTABLE" start "$@"

```
 Just to mention in SuSe and Solaris I could start any shell script in Gnome, but other things didn't work very well and I became a Ubuntu.

---

