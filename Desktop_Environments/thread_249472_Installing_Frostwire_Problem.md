---
title: "Installing Frostwire Problem"
date: 2006-09-02
forum: Desktop Environments
---

### Post by NakedGreekStatue on 2006-09-02
Hey I just installed Ubuntu and updated everything. I am trying to get frostwire to work and it doesnt seem to recognize that I have Java5 installed. I installed Java from the instructions here [http://doc.gwos.org/index.php/DapperGuide#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox](http://doc.gwos.org/index.php/DapperGuide#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox)

But when I try and run Frostwire I get this:

```

nate@flip:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at http://www.java.com
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com

```

any help?

---

### Post by taurus on 2006-09-02
Did you either put the path to where your new java is on your path (or link it) or configure it first?  What do you get when you run this command at the prompt?

```
java -version
```

---

### Post by NakedGreekStatue on 2006-09-02
I got this

```

nate@flip:~$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.0 (Ubuntu 4.1.0-1ubuntu8)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```

---

### Post by NakedGreekStatue on 2006-09-02
No i don't know how to configure it or set the new path. Could you help me?

---

### Post by NakedGreekStatue on 2006-09-02
*bump*

---

### Post by SpongeBob SquarePants on 2006-09-02
Try.....

sudo update-alternatives --config java

.....and choose the option that corresponds to the the Java installation you want to use as default.

---

### Post by hraposo on 2006-09-03
You can instal java and frostwire whit easyubuntu and automatix 
[http://www.getautomatix.com]("http://www.getautomatix.com")

---

