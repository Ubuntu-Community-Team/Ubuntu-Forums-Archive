---
title: "Can't install anything through apt."
date: 2009-04-07
forum: General Help
---

### Post by tom66 on 2009-04-07
Every time I try to install something through apt:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
k3b is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up sun-java6-doc (6-10-0ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] no
Abort installation of JDK documentation
dpkg: error processing sun-java6-doc (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 sun-java6-doc
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

How can I get rid of Java/fix this problem? I can't find the doc zips on Java.**

---

### Post by tom66 on 2009-04-07
Fixed, files here for anyone interested:

[http://www.filewatcher.com/m/jdk-6-doc.zip.54898268.0.0.html](http://www.filewatcher.com/m/jdk-6-doc.zip.54898268.0.0.html)

Java/Sun doesn't seem to host them any more...!

---

### Post by meho_r on 2009-04-07
It's not only java's problem. There are bunch of packages that cause postinistall errors. Kind of solution is as follows:

1. you'll find postinst script here: /var/lib/dpkg/info Look for the one with .postinst extension (i.e. in your case it'll be: sun-java6-doc.postinst or something similar)

2. open it with a text editor and add "exit 0" (without quotes) just few lines down from the beginning of file, immediately after "set -e". You'll need to have root privileges to do this, so go with **gksu gedit**

3. sudo apt-get install -f

---

