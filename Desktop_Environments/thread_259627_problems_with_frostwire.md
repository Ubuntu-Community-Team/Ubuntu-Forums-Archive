---
title: "problems with frostwire"
date: 2006-09-17
forum: Desktop Environments
---

### Post by SpikeyMike on 2006-09-17
Hi

I recently used easyubuntu to supposedly install the necessary updates to my system so I can play audio files, it also installed java, I also installed frostwire but nothing happens when I try to open it, I ran the following command in a terminal: 

cd /usr/lib/frostwire && bash runFrost.sh

and it said that I needed to upgrade to JRE 1.4.x or higher, I checked and I have Java 1.5, any ideas what the problem could be?

Mikey

---

### Post by jpkotta on 2006-09-17
Try ```
update-java-alternatives -l
``` to get all of the Javas installed on your system.  Then set it one that's 1.5 or better with ```
sudo update-java-alternatives -s <up_to_date_java>
```  Don't literally type <up_to_date_java>, type one of the ones the -l command listed.  Probably a Sun Java will work best.

---

### Post by SpikeyMike on 2006-09-24
Don't literally type <up_to_date_java>, type one of the ones the -l command listed.  Probably a Sun Java will work best.[/QUOTE]

Hi

sorry for my late reply, I have been too busy to try it, I tried it today but couldn't get it to work, what exactly do I have to type between the <>? I tried a few alternatives but it kept giving a syntax error, this is what I see when I type the "update-java-alternatives -l" command:

java-1.5.0-sun 53 /usr/lib/jvm/java-1.5.0-sun
java-gcj 1041 /usr/lib/jvm/java-gcj

I tried typing "java-1.5.0-sun" but that didn't work

any help appreciated

Mikey

---

### Post by jazz452 on 2007-09-16
I did this " sudo update-java-alternatives -s /usr/lib/jvm/java-6-sun" and it worked thanks the lot.
(gutsy gibbon)

---

### Post by hyperair on 2007-09-22
I did that and I still get this problem

```
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_02]
Configuring environment...
Loading FrostWire:
java: xcb_xlib.c:50: xcb_xlib_unlock: Assertion `c->xlib.lock' failed.
/usr/lib/frostwire/runFrostwire.sh: line 125: 11104 Aborted                 (core dumped) ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar $ARGUMENTS


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_02"
Java(TM) SE Runtime Environment (build 1.6.0_02-b05)
Java HotSpot(TM) Client VM (build 1.6.0_02-b05, mixed mode, sharing)

```

I'm using Gutsy.

---

### Post by rmtatum on 2007-09-26
I have the same problem as hyperair.

---

### Post by hyperair on 2007-09-26
It's probably one of the custom packages. I tried reinstalling Gutsy, and it worked fine since.

---

### Post by master_kernel on 2007-09-30
Sort of same problem, here's mine, using 64-bit Ubuntu:

> Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_03]
Configuring environment...
Loading FrostWire:
#
# An unexpected error has been detected by Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00002b2b6ae60e25, pid=7406, tid=1076017488
#
# Java VM: Java HotSpot(TM) 64-Bit Server VM (1.6.0_03-b05 mixed mode)
# Problematic frame:
# C  [libc.so.6+0x2fe25]  catgets+0x15
#
# An error report file with more information is saved as /tmp/hs_err_pid7406.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
#
/usr/lib/frostwire/runFrostwire.sh: line 125:  7406 Aborted                 (core dumped) ${JAVA_PROGRAM_DIR}java -ea -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. $EXECUTABLE -jar FrostWire.jar $ARGUMENTS


******************************************************************
Something went wrong with FrostWire.
Maybe you're using the wrong version of Java?
(FrostWire is tested against and works best with with Sun's JRE, Java 1.4+)
The version of Java in your PATH is:
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.6.0_03-b05, mixed mode)


---

### Post by ST.x on 2007-09-30
> **master_kernel said:**
> Sort of same problem, here's mine, using 64-bit Ubuntu:
^ yep I had the same one, just install install java 5 from add/remove, then use:
sudo update-alternatives --config java

Use that to change the default to 1.5 and try running frostwire. It might  not work straight away,  when  I did it it still crashed inside  the frostwire window sometimes, then randomly  started working properly.

---

### Post by hyperair on 2007-10-01
I reinstalled Gutsy and it worked xD

..but before that I downloaded the source code of a whole lot of XCB libraries, and removed the assert lines from the offending one, then compiled the deb and reinstalled.

---

### Post by zachalekos on 2007-10-01
> **jazz452 said:**
> I did this " sudo update-java-alternatives -s /usr/lib/jvm/java-6-sun" and it worked thanks the lot.
(gutsy gibbon)

worked a charm. Thank you

---

### Post by hallowname on 2007-10-01
it was indeed some of Gutsy's x11-xcb issues, but it is now fixed and a lot of wanna-b-fusion users stopped complaining... xcb should have been a 'duh' years ago...

---

### Post by hyperair on 2007-10-02
Figures eh, those were the libraries I patched to get Frostwire working anyway.

---

### Post by Ant1jr on 2007-10-02
Totally uninstall anything that starts with java, as well as frostwire. Reinstall. It worked for me.

EDIT: Nm noticed problem's already solved.

---

### Post by FAttyBones on 2008-04-26
This may not be the best way to do it but it worked for me.

in usr/lib/frostwire

renamed runFrostwire.sh to startFrostwiredisabled.sh

Created a new runFrostwire.sh containing only the following lines

```

#!/bin/bash
cd /usr/lib/frostwire
java -jar FrostWire.jar

```

and commented out all the (unneccessary i hope) lines in /usr/bin/frostwire

```

#!/bin/bash
# export AWT_TOOLKIT=MToolkit
# export HOSTNAME=localhost
/usr/lib/frostwire/runFrostwire.sh

```

Now I installed the deb from the frostwire site and I have sun java 5 as the default jvm.  I don't remember how that was installed, but I have java in my PATH.  How much of that matters I don't know.  I tested searching and downloading.  Oh, and if you run the scripts in the terminal, Java still spits errors, but the program runs.

Edit: This is on 64, so if reinstalling Java and all that doesn't work, this might.

( \________/ )
(_FattyBones_)

---

