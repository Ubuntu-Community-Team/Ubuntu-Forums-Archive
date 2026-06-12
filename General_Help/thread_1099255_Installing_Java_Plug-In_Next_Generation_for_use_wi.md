---
title: "Installing Java Plug-In Next Generation for use with Firefox 3.0"
date: 2009-03-18
forum: General Help
---

### Post by cpudney on 2009-03-18
G'day,

[I wanted to use Sun's Java Plug-In "Next Generation" (NG) with Firefox 3.0]("http://ubuntu-linux-dell-inspiron-9400.blogspot.com/2009/03/java-plug-in-next-generation-with.html") on Hardy. However, at the time of writing the latest packages available in Ubuntu's repositories are sun-java6-*, which correspond to Java 6.0 update 7. This contains the "classic" plug-in; the NG plug-in was introduced in Java 6.0 update 10.

So, I [downloaded the latest Sun JDK]("http://java.sun.com/javase/downloads/index.jsp") - v6.0 update 12 - and installed it in /opt/java. Then I performed the following steps:

[LIST=1]

[*]Create a symbolic link from /usr/lib/jvm to the installed JDK:
```
cd /usr/lib/jvm
sudo ln -s /opt/java/jdk1.6.0_12 java-6u12-sun
```
[*]Created /usr/lib/jvm/.java-6u12-sun.jinfo. I simply copied .java-6-sun and editted (see below).
**Note**, that in order to use the NG rather than "classic" plug-in, I specified /usr/lib/jvm/java-6u12-sun/jre/lib/i386/libnpjp2.so for the *-javaplugin.so alternatives. I also needed to add an entry for firefox-3.0-javaplugin.so, which is missing from .java-6-sun.jinfo.
[*]Installed alternatives for /usr/lib/jvm/java-6u12-sun. For each line of .java-6u12-sun.jinfo I ran update-alternatives --install, e.g.
```
sudo update-alternatives --install \
  /usr/bin/firefox-3.0-javaplugin.so \
  firefox-3.0-javaplugin.so \
  /usr/lib/jvm/java-6u12-sun/jre/lib/i386/libnpjp2.so \
  64
```
Doing this manually is a bit tedious, so I created a Perl script to do - see below.
[*]Selected the java-6u12-sun jav alternative, i.e.
```
sudo update-java-alternatives -s java-6u12-sun
```
[/LIST]
The /usr/lib/.java-6u12-sun.jinfo I created in step 2.

```
name=java-6-sun-1.6.0.12
alias=java-6u12-sun
priority=64
section=non-free

jre ControlPanel /usr/lib/jvm/java-6u12-sun/jre/bin/ControlPanel
jre java /usr/lib/jvm/java-6u12-sun/jre/bin/java
jre java_vm /usr/lib/jvm/java-6u12-sun/jre/bin/java_vm
jre javaws /usr/lib/jvm/java-6u12-sun/jre/bin/javaws
jre jcontrol /usr/lib/jvm/java-6u12-sun/jre/bin/jcontrol
jre keytool /usr/lib/jvm/java-6u12-sun/jre/bin/keytool
jre pack200 /usr/lib/jvm/java-6u12-sun/jre/bin/pack200
jre policytool /usr/lib/jvm/java-6u12-sun/jre/bin/policytool
jre rmid /usr/lib/jvm/java-6u12-sun/jre/bin/rmid
jre rmiregistry /usr/lib/jvm/java-6u12-sun/jre/bin/rmiregistry
jre unpack200 /usr/lib/jvm/java-6u12-sun/jre/bin/unpack200
jre orbd /usr/lib/jvm/java-6u12-sun/jre/bin/orbd
jre servertool /usr/lib/jvm/java-6u12-sun/jre/bin/servertool
jre tnameserv /usr/lib/jvm/java-6u12-sun/jre/bin/tnameserv
jre jexec /usr/lib/jvm/java-6u12-sun/jre/lib/jexec
jdk HtmlConverter /usr/lib/jvm/java-6u12-sun/bin/HtmlConverter
jdk appletviewer /usr/lib/jvm/java-6u12-sun/bin/appletviewer
jdk apt /usr/lib/jvm/java-6u12-sun/bin/apt
jdk extcheck /usr/lib/jvm/java-6u12-sun/bin/extcheck
jdk idlj /usr/lib/jvm/java-6u12-sun/bin/idlj
jdk jar /usr/lib/jvm/java-6u12-sun/bin/jar
jdk jarsigner /usr/lib/jvm/java-6u12-sun/bin/jarsigner
jdk java-rmi.cgi /usr/lib/jvm/java-6u12-sun/bin/java-rmi.cgi
jdk javac /usr/lib/jvm/java-6u12-sun/bin/javac
jdk javadoc /usr/lib/jvm/java-6u12-sun/bin/javadoc
jdk javah /usr/lib/jvm/java-6u12-sun/bin/javah
jdk javap /usr/lib/jvm/java-6u12-sun/bin/javap
jdk jconsole /usr/lib/jvm/java-6u12-sun/bin/jconsole
jdk jdb /usr/lib/jvm/java-6u12-sun/bin/jdb
jdk jhat /usr/lib/jvm/java-6u12-sun/bin/jhat
jdk jinfo /usr/lib/jvm/java-6u12-sun/bin/jinfo
jdk jmap /usr/lib/jvm/java-6u12-sun/bin/jmap
jdk jps /usr/lib/jvm/java-6u12-sun/bin/jps
jdk jrunscript /usr/lib/jvm/java-6u12-sun/bin/jrunscript
jdk jsadebugd /usr/lib/jvm/java-6u12-sun/bin/jsadebugd
jdk jstack /usr/lib/jvm/java-6u12-sun/bin/jstack
jdk jstat /usr/lib/jvm/java-6u12-sun/bin/jstat
jdk jstatd /usr/lib/jvm/java-6u12-sun/bin/jstatd
jdk jvisualvm /usr/lib/jvm/java-6u12-sun/bin/jvisualvm
jdk native2ascii /usr/lib/jvm/java-6u12-sun/bin/native2ascii
jdk rmic /usr/lib/jvm/java-6u12-sun/bin/rmic
jdk schemagen /usr/lib/jvm/java-6u12-sun/bin/schemagen
jdk serialver /usr/lib/jvm/java-6u12-sun/bin/serialver
jdk wsgen /usr/lib/jvm/java-6u12-sun/bin/wsgen
jdk wsimport /usr/lib/jvm/java-6u12-sun/bin/wsimport
jdk xjc /usr/lib/jvm/java-6u12-sun/bin/xjc
plugin xulrunner-1.9-javaplugin.so /usr/lib/jvm/java-6u12-sun/jre/lib/i386/libnpjp2.so
plugin firefox-javaplugin.so /usr/lib/jvm/java-6u12-sun/jre/lib/i386/libnpjp2.so
plugin firefox-3.0-javaplugin.so /usr/lib/jvm/java-6u12-sun/jre/lib/i386/libnpjp2.so
plugin iceape-javaplugin.so /usr/lib/jvm/java-6u12-sun/jre/lib/i386/libnpjp2.so
plugin iceweasel-javaplugin.so /usr/lib/jvm/java-6u12-sun/jre/lib/i386/libnpjp2.so
plugin mozilla-javaplugin.so /usr/lib/jvm/java-6u12-sun/jre/lib/i386/libnpjp2.so
plugin midbrowser-javaplugin.so /usr/lib/jvm/java-6u12-sun/jre/lib/i386/libnpjp2.so
plugin xulrunner-javaplugin.so /usr/lib/jvm/java-6u12-sun/jre/lib/i386/libnpjp2.so
```

The perl-script used in step 3. above. Copy-and-paste into /tmp/java6u12sun.pl then:

```
cd /tmp
chmod +x java6u12sun.pl
sudo ./java6u12sun.pl
```

```
#!/usr/bin/perl

use strict;

# Read .jinfo file.
my @lines = ();
open(JINFO, '/usr/lib/jvm/.java-6u12-sun.jinfo')
   or die "Can't open .jinfo file.";
@lines = ;
close(JINFO);

# Install alternatives.
for (@lines)
{
   if ($_=~ m+/usr/lib/jvm/java-6u12-sun+)
   {
 my @split = split ' ', $_;
 system "update-alternatives --install /usr/bin/@split[1]  @split[1]  @split[2] 64";
   }
}

1;
```

---

