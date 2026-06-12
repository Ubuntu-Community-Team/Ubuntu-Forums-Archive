---
title: "Java 1.4 Installation"
date: 2009-02-15
forum: General Help
---

### Post by bigoperm on 2009-02-15
I already have the sun-java6 package installed; however, I need Java 1.4 as well. I've downloaded and extracted the bin file from the Sun website to my machine, placing it in the /usr/lib/jvm alongside java 1.6, and added a .jinfo file
```
$> ls -lA
total 16
drwxrwxr-x 9 root   root   4096 2009-02-13 09:29 j2sdk1.4.2_18
lrwxrwxrwx 1 root   root     13 2009-02-13 11:50 java-4-sun -> j2sdk1.4.2_18
-rw-r--r-- 1 sensor sensor 1377 2009-02-13 15:01 .java-4-sun.jinfo
lrwxrwxrwx 1 root   root     19 2009-02-09 14:50 java-6-sun -> java-6-sun-1.6.0.06
drwxr-xr-x 8 root   root   4096 2009-02-09 14:50 java-6-sun-1.6.0.06
-rw-r--r-- 1 root   root   2341 2008-04-17 02:07 .java-6-sun.jinfo
```
The jinfo file for Java 1.4 was copied from the 1.6 version, with programs files that did not exist removed (thus, every entry in the Java 1.4 info file exists and is executable. However, when running update-java-alternatives I get the following errors
```
$> sudo update-java-alternatives -s java-4-sun
No alternatives for xulrunner-addons-javaplugin.so.
update-alternatives: Cannot find alternative `/usr/lib/jvm/java-4-sun/bin/appletviewer'.

update-alternatives: Cannot find alternative `/usr/lib/jvm/java-4-sun/bin/extcheck'.

update-alternatives: Cannot find alternative `/usr/lib/jvm/java-4-sun/bin/HtmlConverter'.

update-alternatives: Cannot find alternative `/usr/lib/jvm/java-4-sun/bin/idlj'.

update-alternatives: Cannot find alternative `/usr/lib/jvm/java-4-sun/bin/jarsigner'.

update-alternatives: Cannot find alternative `/usr/lib/jvm/java-4-sun/bin/jar'.

update-alternatives: Cannot find alternative `/usr/lib/jvm/java-4-sun/bin/javac'.

update-alternatives: Cannot find alternative `/usr/lib/jvm/java-4-sun/bin/javadoc'.

update-alternatives: Cannot find alternative `/usr/lib/jvm/java-4-sun/bin/javah'.

update-alternatives: Cannot find alternative `/usr/lib/jvm/java-4-sun/bin/javap'.

update-alternatives: Cannot find alternative `/usr/lib/jvm/java-4-sun/bin/java-rmi.cgi'.

update-alternatives: Cannot find alternative `/usr/lib/jvm/java-4-sun/bin/jdb'.

update-alternatives: Cannot find alternative `/usr/lib/jvm/java-4-sun/bin/jmap'.

update-alternatives: Cannot find alternative `/usr/lib/jvm/java-4-sun/bin/native2ascii'.

update-alternatives: Cannot find alternative `/usr/lib/jvm/java-4-sun/bin/rmic'.

update-alternatives: Cannot find alternative `/usr/lib/jvm/java-4-sun/bin/serialver'.

update-alternatives: Cannot find alternative `/usr/lib/jvm/java-4-sun/jre/bin/ControlPanel'.

update-alternatives: Cannot find alternative `/usr/lib/jvm/java-4-sun/jre/bin/java'.

update-alternatives: Cannot find alternative `/usr/lib/jvm/java-4-sun/jre/bin/java_vm'.

update-alternatives: Cannot find alternative `/usr/lib/jvm/java-4-sun/jre/bin/keytool'.

update-alternatives: Cannot find alternative `/usr/lib/jvm/java-4-sun/jre/bin/orbd'.

update-alternatives: Cannot find alternative `/usr/lib/jvm/java-4-sun/jre/bin/policytool'.

update-alternatives: Cannot find alternative `/usr/lib/jvm/java-4-sun/jre/bin/rmid'.

update-alternatives: Cannot find alternative `/usr/lib/jvm/java-4-sun/jre/bin/rmiregistry'.

update-alternatives: Cannot find alternative `/usr/lib/jvm/java-4-sun/jre/bin/servertool'.

update-alternatives: Cannot find alternative `/usr/lib/jvm/java-4-sun/jre/bin/tnameserv'.
```
which is confusing, because each path is valid. For example
```
$> ls /usr/lib/jvm/java-4-sun/jre/bin/tnameserv
/usr/lib/jvm/java-4-sun/jre/bin/tnameserv
```

Any assistance would be greatly appreciated. Thanks in advance.

jerome

---

