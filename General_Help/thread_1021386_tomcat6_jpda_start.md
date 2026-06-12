---
title: "tomcat6 jpda start?"
date: 2008-12-25
forum: General Help
---

### Post by putnins on 2008-12-25
I've installed the stock tomcat6 package on Intrepid, and I want to configure it for remote JPDA debugging (listening on port 8000) for debugging a webapp from eclipse. The normal way to do this is to edit /usr/share/tomcat6/bin/startup.sh so it starts in debug mode:

exec "$PRGDIR"/"$EXECUTABLE" jpda start "$@"

However, the Ubuntu system startup script doesn't seem to follow the normal tomcat6 startup procedure. /etc/init.d/tomcat6 runs /usr/bin/jsvc instead of executing the normal startup scripts in /usr/share/tomcat6/bin:

DAEMON=/usr/bin/jsvc
.
.
.
 $DAEMON -user "$TOMCAT6_USER" -cp "$JSVC_CLASSPATH" \
                    -outfile SYSLOG -errfile SYSLOG \
                    -pidfile "$CATALINA_PID" $JAVA_OPTS "$BOOTSTRAP_CLASS"

How should I configure it to start the debugger?

---

### Post by pmeade@guild.com on 2009-02-04
I encountered a similar need yesterday with Tomcat 5.5. My solution was to graft a piece of the catalina.sh script into the init.d script provided by Ubuntu. (/etc/init.d/tomcat5.5)

```
# Look for Java Secure Sockets Extension (JSSE) JARs
if [ -z "${JSSE_HOME}" -a -r "${JAVA_HOME}/jre/lib/jsse.jar" ]; then
    JSSE_HOME="${JAVA_HOME}/jre/"
fi
export JSSE_HOME

# start the jpda remote debugger
if [ -z "$JPDA_TRANSPORT" ]; then
    JPDA_TRANSPORT="dt_socket"
fi
if [ -z "$JPDA_ADDRESS" ]; then
    JPDA_ADDRESS="8000"
fi
if [ -z "$JPDA_SUSPEND" ]; then
    JPDA_SUSPEND="n"
fi
if [ -z "$JPDA_OPTS" ]; then
    JPDA_OPTS="-Xdebug -Xrunjdwp:transport=$JPDA_TRANSPORT,address=$JPDA_ADDRESS,server=y,suspend=$JPDA_SUSPEND"
fi

JAVA_OPTS="$JAVA_OPTS $JPDA_OPTS"
# end jpda remote debugger changes

case "$1" in
  start)
        if [ -z "$JAVA_HOME" ]; then
                log_failure_msg "no JDK found - please set JAVA_HOME"
                exit 1
        fi

```

Hopefully I've provided enough context that you could do something similar with your script.

<Insert all the standard disclaimers about it working for me but your milage may vary, and security risks of exposing a debugger in a production environment, etc.>

---

### Post by bedge on 2009-05-11
Here's a patch against the jaunty tomcat6 init.d script that enables:
   "/etc/init.d/tomcat start jpda"

```

diff -Naur $BUILD_ROOT/etc/init.d/tomcat6 $BUILD_ROOT/etc/init.d/tomcat6d

--- /etc/init.d/tomcat6.old  2009-05-11 14:00:35.000000000 -0700
+++ /etc/init.d/tomcat6      2009-05-11 14:46:55.000000000 -0700
@@ -43,6 +43,12 @@
 . /lib/lsb/init-functions
 . /etc/default/rcS

+if [ "$2" = "jpda" ]
+then
+        JPDA_OPTS="-Xdebug -Xrunjdwp:transport=dt_socket,address=8000,server=y,suspend=n"
+fi
+CATALINA_OPTS="$JPDA_OPTS"
+

 # The following variables can be overwritten in $DEFAULT

@@ -65,7 +71,7 @@
 CATALINA_BASE=/var/lib/$NAME

 # Use the Java security manager? (yes/no)
-OMCAT6_SECURITY=yes
+TOMCAT6_SECURITY=yes

 # Default Java options
 # Set java.awt.headless=true if JAVA_OPTS is not set so the
@@ -158,6 +164,7 @@

                $DAEMON -user "$TOMCAT6_USER" -cp "$JSVC_CLASSPATH" \
                    -outfile SYSLOG -errfile SYSLOG \
+                       $CATALINA_OPTS \
                    -pidfile "$CATALINA_PID" $JAVA_OPTS "$BOOTSTRAP_CLASS"

                sleep 5

```
I'm sure there's more one could add, but this got me going.

-Bruce

---

### Post by bedge on 2009-05-11
While the prev post got me going again, for a bit, it seems like the ubuntu packaged tomcat6 has other problems too.
Every time I get past something I hit another that makes me go back to the apache tgz instead. 
Well, I've flipped enough times now that it's clear that either
a) I don't know enough about the ubuntu maintainer's goals to be able to use it, or 
b) The apache tgz is just much more user friendly and simple to setup.

Here's a simple start-stop script for the apache one you can drop into init.d (if you put it somewhere other than usr/local/tomcat you'll need to fix that bit) :



```
#!/bin/bash

PATH=/bin:/sbin:/usr/bin:/usr/sbin:/usr/local/bin:/usr/kahuna/bin:/usr/local/sbin
export PATH                                                                      

test -x $DAEMON || exit 0
if [ $DEBUG_WEBAPPS ] ; then
        true
else
        true
fi

NAME=tomcat
TOMCAT_HOME=/usr/local/$NAME
DAEMON_START=$TOMCAT_HOME/bin/startup.sh
DAEMON_STOP=$TOMCAT_HOME/bin/shutdown.sh


case "$1" in
  start)
                echo "Starting $NAME ..."
                $DAEMON_START
                echo $! > /var/run/$NAME.pid
                ;;

  stop)
                echo "Stopping $NAME ..."
                $DAEMON_STOP
                ;;

  restart|reload)
                $0 stop
                sleep 2
                $0 start
                RETVAL=$?
                ;;

  *)
                echo "Usage: $0 {start|stop|restart}"
                RETVAL=1
                ;;
esac

exit $RETVAL


```


Yeah, I know, "I could have done that"... but perhaps someone won't have to.

-Bruce

---

### Post by scott.robertson on 2010-04-28
It seems like this has been resolved by allowing you to uncomment the following line in /etc/default/tomcat6
```
JAVA_OPTS="${JAVA_OPTS} -Xdebug
-Xrunjdwp:transport=dt_socket,address=8000,server=y,suspend=n"

```

This may only be in lucid and newer ([_patch notification on mailing list_]("https://lists.ubuntu.com/archives/lucid-changes/2009-December/001778.html"))

---

### Post by chris2107 on 2010-07-17
Thanks Scott,
 you post helped me a lot.

---

