---
title: "how do I check if java is installed?"
date: 2006-02-09
forum: Desktop Environments
---

### Post by yb1011 on 2006-02-09
Hey guys,
Ive been using Ubuntu for a while now and need some help.
How do I check if java is installed? I first tried one of the how-to's in the forum and when that did not work...I tried Automatix. Automatix installed everything perfectly and tells me that everything is installed..but how to I check for java?
I tried typing java-version in the terminal but it gives me :command not found.

And when I try: sudo update-alternatives --config java I get 

```
There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
*+    2        /usr/lib/jvm/java-gcj/bin/java
      3        /usr/local/jre1.5.0_06/bin/java
      4        /usr/lib/j2re1.5-sun/bin/java

```
How should I proceed?

---

### Post by ajgreeny on 2006-02-09
Look in synaptic.  Open it and search for java and see what is marked as installed; that should give you a good idea of what is there.

---

### Post by taurus on 2006-02-09
Or

sudo find / -name java -print

---

### Post by yb1011 on 2006-02-09
First of all.. thank you for your replies.
When I do
[QUOTE=taurus]sudo find / -name java -print[/QUOTE]
I get 
> /media/hda1/Program Files/OpenOffice.org 2.0/share/Scripts/java
/media/hda1/WINDOWS/java
/etc/alternatives/java
/var/lib/dpkg/alternatives/java
/usr/share/java
/usr/share/opera/java
/usr/bin/java
/usr/include/mozilla-firefox/java
/usr/lib/jvm/java-1.4.2-gcj-4.0-1.4.2.0/bin/java
/usr/lib/jvm/java-1.4.2-gcj-4.0-1.4.2.0/jre/bin/java
/usr/lib/j2re1.5-sun/bin/java
/usr/local/jre1.5.0_06/bin/java
find: WARNING: Hard link count is wrong for /proc: this may be a bug in your filesystem driver.  Automatically turning on find's -noleaf option.  Earlier results may have failed to include directories that should have been searched.
find: /proc/8117/task: No such file or directory
find: /proc/8117/fd: No such file or directory
find: /proc/18647/task: No such file or directory
find: /proc/18647/fd: No such file or directory


What does this mean? can someone please put this in layman terms.... does this mean java is installed? if so then why does typing "java-version" not give me any result?
Please suggest. thankyou,

---

### Post by Almighty on 2006-02-09
Or you can cheat by going  here [http://www.java.com/en/download/installed.jsp?detect=jre&try=1]("http://www.java.com/en/download/installed.jsp?detect=jre&try=1")

---

### Post by yb1011 on 2006-02-09
thanks almighty (LOL) when i do that I get:
> Description:Your Environment
Java Runtime Vendor:Sun Microsystems Inc.
Java Runtime Version:1.5.0_05
So I guess Im good to go... but why does "java-version" in the terminal give me nothing? 
PS- I stress upon making sure that I have java because right now I have high-speed internet but after this week I'll only be on dialup...so Im trying to get all that I can while I can!!!
thanks guys!

---

### Post by taurus on 2006-02-09
Did you remember to put a space between a and - like

java -version

However, it looks like you have one in /usr/bin/java and another copy in /usr/local/jre1.5.0_06/bin/java...  I assume /usr/bin/java is a link to usr/local/jre1.5.0_06/bin/java then!

---

### Post by yb1011 on 2006-02-09
> java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) Client VM (build 1.5.0_05-b05, mixed mode, sharing)

oh man... I did not know about the space. got it! thanks taurus.

thanks for all your help guys! I guess im all good to go.... ISSUE SOLVED!

---

