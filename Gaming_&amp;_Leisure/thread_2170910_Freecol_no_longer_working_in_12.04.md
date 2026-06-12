---
title: "Freecol no longer working in 12.04"
date: 2013-08-28
forum: Gaming &amp; Leisure
---

### Post by Keith_Beef on 2013-08-28
Well, freecol starts, but after I set the difficulty and then select OK, nothing happens other than the sound starts to get choppy.

I tried starting from a terminal window, this is what I see.
```

$ freecol --no-intro --windowed
[warning] /usr/games/freecol: No java runtime was found
[warning] /usr/games/freecol: No JAVA_CMD set for run_java, falling back to JAVA_CMD = java
```

I looked at the run script; the important line is:
```
run_java -Xmx180M -Dsun.java2d.pmoffscreen=false net.sf.freecol.FreeCol --freecol-data \
    /usr/share/games/freecol $lang_argument "$@"
``` 

Java version:
```
$ java -version
java version "1.7.0_25"
Java(TM) SE Runtime Environment (build 1.7.0_25-b15)
Java HotSpot(TM) 64-Bit Server VM (build 23.25-b01, mixed mode)

```

---

### Post by DarkAmbient on 2013-08-28
Could you post the entire run-script?

---

### Post by zKhtdyX on 2013-11-20
Freeciv 0.10.7 stopps working while playing the intro video right after startup. (ubuntu 12.04)

```
$ java -version 
java version "1.7.0_45"
Java(TM) SE Runtime Environment (build 1.7.0_45-b18)
Java HotSpot(TM) Server VM (build 24.45-b08, mixed mode)

```


```
#! /bin/sh
# Generic freecol start script.
# Please customize this for your distribution.
# Look at the ../debian script for other ideas, they are clueful.
#
# Things this script needs to do:
# - Find the freecol data directory.
#     It is usually called "data".
#     Try to allow the --freecol-data command line override to work.
#     This script allows a FREECOL_DATA environment variable override,
#     tries the obvious directories, and puts the result in FCDAT.
# - Find the freecol .jar.
#     It is usually called "FreeCol.jar".
#     This script allows a FREECOL_JAR environment variable override,
#     tries the obvious directories, and puts the result in FCJAR.
# - Find the java binary.
#     This script assumes it is "java".
#     If not, fix the last line.
#
BINDIR=`dirname "$0"`
FREECOLDATA="data"
FREECOLJAR="FreeCol.jar"

# Find the data directory, put it in FCDAT.
FCDAT=""
# Is the data directory supplied in the command line args?
for x in $@ ; do
    if test "x$x" = "x--freecol-data" ; then
        FCDAT="DONTSET!"
        break
    fi
done
# - Is there a credible FREECOL_DATA environment variable?
if test "x${FCDAT}" = "x" ; then
    if test "x${FREECOL_DATA}" != "x" -a -d "${FREECOL_DATA}" ; then
        FCDAT="${FREECOL_DATA}"
# - Is it in the current directory?
    elif test -d "${FREECOLDATA}" ; then
        FCDAT="DONTSET!"
# - Is it where this script is?
    elif test -d "${BINDIR}/${FREECOLDATA}" ; then
        FCDAT="${BINDIR}/${FREECOLDATA}"
# - Is it in a likely linux FHS place?
    elif test -d "/usr/share/freecol/data" ; then
        FCDAT="/usr/share/freecol/data"
# - It it in $HOME/freecol?
    elif test "x${HOME}" != "x" -a -d "${HOME}/freecol" \
           -a -d "${HOME}/freecol/${FREECOLDATA}" ; then
        FCDAT="${HOME}/freecol/${FREECOLDATA}"
# - Give up.
    else
        echo "can not find freecol data directory" >&2
        exit 1
    fi
fi

# Find the freecol jar, put it in FCJAR.
FCJAR=""
# - Is there a credible FREECOL_JAR environment variable?
if test "x${FREECOL_JAR}" != "x" -a -r "${FREECOL_JAR}" ; then
    FCJAR="${FREECOL_JAR}"
# - Is it in the current directory?
elif test -r "${FREECOLJAR}" ; then
    FCJAR="${FREECOLJAR}"
# - Is it where this script is?
elif test -r "${BINDIR}/${FREECOLJAR}" ; then
    FCJAR="${BINDIR}/${FREECOLJAR}"
# - Is it in a likely linux FHS place?
elif test -d "/usr/share/java/${FREECOLJAR}" ; then
    FCJAR="/usr/share/java/${FREECOLJAR}"
# Give up.
else
    echo "can not find ${FREECOLJAR}" >&2
    exit 1
fi

# Clean up the data argument and run.
if test "x${FCDAT}" = "xDONTSET!" ; then
    exec java -Xmx512M -cp "${FCJAR}" net.sf.freecol.FreeCol ${1+"$@"}
else
    exec java -Xmx512M -cp "${FCJAR}" net.sf.freecol.FreeCol --freecol-data "${FCDAT}" ${1+"$@"}
fi
```

---

