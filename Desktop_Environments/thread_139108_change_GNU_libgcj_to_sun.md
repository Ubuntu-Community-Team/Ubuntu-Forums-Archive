---
title: "change GNU libgcj to sun?"
date: 2006-03-03
forum: Desktop Environments
---

### Post by dnis on 2006-03-03
Hi!

I just wrote my self a little HelloWorld Java swing window which I turned in to a jar file in Netbeans with Sun's java environment. But when I try to run i in the shell with:

java -jar test.jar

i get this error message:

** ERROR **: file ../../../src/libjava/jni/gtk-peer/gnu_java_awt_peer_gtk_GtkImage.c: line 572 (createRawData): assertion failed: (data_fid != 0)
aborting...
Aborted

I checked the java version with:

java -verison and got:

java version "1.4.2"
gij (GNU libgcj) version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)

What is the problem? should i change to Sun instead of GNU libgcj to make it work? 

thanks!

---

### Post by zzxop on 2006-05-10
sudo update-alternatives --config java

---

