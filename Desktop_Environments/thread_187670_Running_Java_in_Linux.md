---
title: "Running Java in Linux"
date: 2006-06-03
forum: Desktop Environments
---

### Post by irv on 2006-06-03
This question deals with running Java programs in ubuntu linux. The last issue of Tux mag had an article on &#8220;Learning Foreign Languages with jVLT and StarDict&#8221;. I downloaded the .jar file. and it said to run it, just run java and this file. Here's what I get when I do this in a terminal.

$ java jvlt-0.8.2.jar
Exception in thread "main" java.lang.NoClassDefFoundError: jvlt-0.8.2.jar
   at gnu.java.lang.MainThread.run(libgcj.so.7)
Caused by: java.lang.ClassNotFoundException: jvlt-0.8.2.jar
   at java.lang.Class.forName(libgcj.so.7)
   at gnu.java.lang.MainThread.run(libgcj.so.7)

Does this mean something is wrong with the .jar file, or am I missing a lib file in java?

I tried this and got this: added the -jar befor the file.

$ java -jar jvlt-0.8.2.jar
/home/irv/.jvltrc (No such file or directory)
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   at java.awt.Font.tk(libgcj.so.7)
   at java.awt.Font.getPeerFromToolkit(libgcj.so.7)
   at java.awt.Font.<init>(libgcj.so.7)
   at JVLTUI.main(Unknown Source)
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.gtk.GtkToolkit
   at java.lang.Class.forName(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   ...4 more

---

### Post by meng on 2006-06-03
I'm not sure if this is relevant to your problem, but in order to run out of a .jar, I have to use this syntax:

java -jar <name of jar file>

---

### Post by irv on 2006-06-03
I tried this.

---

### Post by ebash on 2006-06-03
To execute a jar use the following command:
```
java -jar  jvlt-0.8.2.jar
```

---

### Post by meng on 2006-06-03
I did see your previous thread, so you may already have done this, but can you confirm that the sun java is your default java?

sudo update-alternatives --config java

---

### Post by irv on 2006-06-03
$ sudo update-alternatives --config java
Password:

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
      2        /usr/bin/gij-wrapper-4.1
*+    3        /usr/lib/jvm/java-gcj/jre/bin/java

Press enter to keep the default[*], or type selection number: 3
Using `/usr/lib/jvm/java-gcj/jre/bin/java' to provide `java'.

#3 is my default. Is this right?

---

### Post by meng on 2006-06-03
Okay, here's my experience:
```
meng@atticus:~$ sudo update-alternatives --config java
Password:

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*     1        /usr/lib/j2sdk1.5-sun/bin/java
      2        /usr/bin/gij-wrapper-4.1
 +    3        /usr/lib/jvm/java-gcj/jre/bin/java

Press enter to keep the default[*], or type selection number: 3
Using `/usr/lib/jvm/java-gcj/jre/bin/java' to provide `java'.
meng@atticus:~$ java -jar jvlt-0.8.2.jar
/home/meng/.jvltrc (No such file or directory)
createDefaultRoot not implemented
fireChangedUpdate not implemented
Exception during event dispatch:
java.util.MissingResourceException: Key 'DISPOSE_ON_CLOSE'not found in Bundle: java.util.PropertyResourceBundle
   at java.util.ResourceBundle.getObject(libgcj.so.7)
   at java.util.ResourceBundle.getString(libgcj.so.7)
   at GUIUtils.getString(Unknown Source)
   at GUIUtils.getString(Unknown Source)
   at GUIUtils.createTextAction(Unknown Source)
   at AbstractDialog.init(Unknown Source)
   at AbstractDialog.setButtons(Unknown Source)
   at EntryQueryDialog.init(Unknown Source)
   at EntryQueryDialog.<init>(Unknown Source)
   at EntryQueryDialog.<init>(Unknown Source)
   at EntryPanel.init(Unknown Source)
   at EntryPanel.<init>(Unknown Source)
   at JVLTUI.initUI(Unknown Source)
   at JVLTUI.access$500(Unknown Source)
   at JVLTUI$6.run(Unknown Source)
   at java.awt.event.InvocationEvent.dispatch(libgcj.so.7)
   at java.awt.EventQueue.dispatchEvent(libgcj.so.7)
   at java.awt.EventDispatchThread.run(libgcj.so.7)
<I had to ctrl-c to escape from here, it wouldn't run>
meng@atticus:~$ sudo update-alternatives --config java

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/lib/j2sdk1.5-sun/bin/java
      2        /usr/bin/gij-wrapper-4.1
*+    3        /usr/lib/jvm/java-gcj/jre/bin/java

Press enter to keep the default[*], or type selection number: 1
Using `/usr/lib/j2sdk1.5-sun/bin/java' to provide `java'.
meng@atticus:~$ java -jar jvlt-0.8.2.jar
/home/meng/.jvltrc (No such file or directory)
meng@atticus:~$
```

By the way, the last "error" is just a message that there wasn't a configuration folder because I was running for the first time and so it was creating the folder for me (sorry for stating the obvious).

So in summary, it didn't work the first time under your java option but it did work the second time when sun java was selected. The next question is why sun java doesn't appear under your list of alternatives. I don't know why off the top of my head. I'll look into it, or maybe someone cleverer will come along.

---

### Post by Antman on 2006-06-03
[QUOTE=irv]$ sudo update-alternatives --config java
Password:

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
      2        /usr/bin/gij-wrapper-4.1
*+    3        /usr/lib/jvm/java-gcj/jre/bin/java

Press enter to keep the default[*], or type selection number: 3
Using `/usr/lib/jvm/java-gcj/jre/bin/java' to provide `java'.

#3 is my default. Is this right?[/QUOTE]

If you go to Applications>Add/Remove and enable "Show Unsupported", you will be able to install Sun's Java 5.0 Runtime. Then select it using the method you used above.

---

### Post by meng on 2006-06-03
(Antman == someoneCleverer)

---

### Post by irv on 2006-06-03
[QUOTE=meng]Okay, here's my experience:
```
meng@atticus:~$ sudo update-alternatives --config java
Password:

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*     1        /usr/lib/j2sdk1.5-sun/bin/java
      2        /usr/bin/gij-wrapper-4.1
 +    3        /usr/lib/jvm/java-gcj/jre/bin/java

Press enter to keep the default[*], or type selection number: 3
Using `/usr/lib/jvm/java-gcj/jre/bin/java' to provide `java'.
meng@atticus:~$ java -jar jvlt-0.8.2.jar
/home/meng/.jvltrc (No such file or directory)
createDefaultRoot not implemented
fireChangedUpdate not implemented
Exception during event dispatch:
java.util.MissingResourceException: Key 'DISPOSE_ON_CLOSE'not found in Bundle: java.util.PropertyResourceBundle
   at java.util.ResourceBundle.getObject(libgcj.so.7)
   at java.util.ResourceBundle.getString(libgcj.so.7)
   at GUIUtils.getString(Unknown Source)
   at GUIUtils.getString(Unknown Source)
   at GUIUtils.createTextAction(Unknown Source)
   at AbstractDialog.init(Unknown Source)
   at AbstractDialog.setButtons(Unknown Source)
   at EntryQueryDialog.init(Unknown Source)
   at EntryQueryDialog.<init>(Unknown Source)
   at EntryQueryDialog.<init>(Unknown Source)
   at EntryPanel.init(Unknown Source)
   at EntryPanel.<init>(Unknown Source)
   at JVLTUI.initUI(Unknown Source)
   at JVLTUI.access$500(Unknown Source)
   at JVLTUI$6.run(Unknown Source)
   at java.awt.event.InvocationEvent.dispatch(libgcj.so.7)
   at java.awt.EventQueue.dispatchEvent(libgcj.so.7)
   at java.awt.EventDispatchThread.run(libgcj.so.7)
<I had to ctrl-c to escape from here, it wouldn't run>
meng@atticus:~$ sudo update-alternatives --config java

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/lib/j2sdk1.5-sun/bin/java
      2        /usr/bin/gij-wrapper-4.1
*+    3        /usr/lib/jvm/java-gcj/jre/bin/java

Press enter to keep the default[*], or type selection number: 1
Using `/usr/lib/j2sdk1.5-sun/bin/java' to provide `java'.
meng@atticus:~$ java -jar jvlt-0.8.2.jar
/home/meng/.jvltrc (No such file or directory)
meng@atticus:~$
```

By the way, the last "error" is just a message that there wasn't a configuration folder because I was running for the first time and so it was creating the folder for me (sorry for stating the obvious).

So in summary, it didn't work the first time under your java option but it did work the second time when sun java was selected. The next question is why sun java doesn't appear under your list of alternatives. I don't know why off the top of my head. I'll look into it, or maybe someone cleverer will come along.[/QUOTE]

Just for the record here is my last results. I guess it over my head what is going on!](*,) 

irv@ubuntu:~/jVLT$ sudo update-alternatives --config java
Password:

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
      2        /usr/bin/gij-wrapper-4.1
*+    3        /usr/lib/jvm/java-gcj/jre/bin/java

Press enter to keep the default[*], or type selection number: 3
Using `/usr/lib/jvm/java-gcj/jre/bin/java' to provide `java'.

irv@ubuntu:~/jVLT$ java -jar jvlt-0.8.2.jar
/home/irv/.jvltrc (No such file or directory)
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   at java.awt.Font.tk(libgcj.so.7)
   at java.awt.Font.getPeerFromToolkit(libgcj.so.7)
   at java.awt.Font.<init>(libgcj.so.7)
   at JVLTUI.main(Unknown Source)
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.gtk.GtkToolkit
   at java.lang.Class.forName(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   ...4 more
irv@ubuntu:~/jVLT$

---

### Post by meng on 2006-06-03
To clarify, the point of my previous post was that if I choose your current default java (which isn't Sun), then I get the same errors, whereas if I choose Sun's java, it works fine.

I know you installed Sun's java, but your system doesn't know that, so it doesn't give you the option of choosing it as default. One way around this problem would be to reinstall Sun's java using the method that Antman suggested.

---

### Post by irv on 2006-06-03
[QUOTE=Antman]If you go to Applications>Add/Remove and enable "Show Unsupported", you will be able to install Sun's Java 5.0 Runtime. Then select it using the method you used above.[/QUOTE]
I don't have Applications>Add/Remove and enable on the Applications menu?

---

### Post by meng on 2006-06-03
You don't have Add/Remove (or perhaps Add Applications) right at the bottom of the Applications menu?????

---

### Post by irv on 2006-06-03
[QUOTE=meng]You don't have Add/Remove (or perhaps Add Applications) right at the bottom of the Applications menu?????[/QUOTE]
No, the last thing I have is "System Tools". I am using Alacarte Menu Editor and it might have removed the Add Applications.

---

### Post by irv on 2006-06-03
[QUOTE=meng]To clarify, the point of my previous post was that if I choose your current default java (which isn't Sun), then I get the same errors, whereas if I choose Sun's java, it works fine.

I know you installed Sun's java, but your system doesn't know that, so it doesn't give you the option of choosing it as default. One way around this problem would be to reinstall Sun's java using the method that Antman suggested.[/QUOTE]
I see you are using 1.5, the only one I could find is 1.4 and it doesn't seem to work. Did you get your 1.5 from Java site?

---

### Post by meng on 2006-06-03
Okay, well admittedly I had found Add Applications buggy and superfluous in Breezy. Anyhow, you could do the same by going to Synaptic and selecting sun-java5-bin package for installation, assuming you have the correct repositories (multiverse) enabled.

EDIT: Yes I got 1.5 from Java site. x86 architecture.

---

### Post by irv on 2006-06-03
[QUOTE=meng]Okay, well admittedly I had found Add Applications buggy and superfluous in Breezy. Anyhow, you could do the same by going to Synaptic and selecting sun-java5-bin package for installation, assuming you have the correct repositories (multiverse) enabled.

EDIT: Yes I got 1.5 from Java site. x86 architecture.[/QUOTE]
I found the RPM file for 1.5 Java so I tried:

irv@ubuntu:~$ sudo alien jre-1_5_0_07-linux-i586.rpm
Password:
Warning: Skipping conversion of scripts in package jre: postinst postrm prerm
Warning: Use the --scripts parameter to include the scripts.

Not sure what -scripts parameter to include with the scripts? Did you install this way.
I was trying to create a .deb file for the install.

---

### Post by meng on 2006-06-03
I would only use alien as a last resort. For your situation, I would suggest:
1. installing from repositories
2. installing from the .bin if (1) doesn't work, preferably using the fakeroot/checkinstall method

(1) seems to be the most popular option these days, but I installed java quite some time ago before it was in the repositories

---

### Post by irv on 2006-06-03
My last post. I have Java 5 installed and the jVLT runs great.
Thanks to all who helped along the way and I hope others who have this problem finds this thread and it helps them.
And special thanks to meng, you were a great help.

---

### Post by meng on 2006-06-03
Pleasure to hear about your success. My Linux knowledge is limited, so I don't get very many opportunities to solve problems.

---

### Post by t0mc4t on 2006-06-03
Hi there...
I have install the sun java version 1.5 update 7. I extract all those file and put it on /usr/lib/java/jre....... It success, and I can run azureus and netbeans on it.
But when I type sudo update-alternative --config java , why I can't see the sun java that I have install? Is there some command that I have to do first before doing the update-alternative command?
Thanks...

---

### Post by mikebai1990 on 2006-08-22
Same question here. I have not been able to succesfully view my newly installed Java 1.5.0_08. Is there a directory I have to put it into for the 'update-alternatives' to see it?

---

### Post by mikebai1990 on 2006-08-22
Ok, I just got it: I used 'sudo apt-get install sun-java5-jre sun-java5-plugin' and then 'sudo update-alternatives --set java /usr/lib/jvm/java-1.5.0-sun/jre/bin/java'.

---

### Post by elbeasto on 2006-09-03
Hey, thanks for that :-)

---

### Post by nanbudh on 2007-04-29
i am facing the same problem. please help

---

### Post by Simon-au on 2007-11-10
Cannot load AWT toolkit fixed by running java config and selecting sun java

sudo update-alternatives --config java

There are 5 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
          2    /usr/bin/gij-4.2
*+        3    /usr/lib/jvm/java-gcj/jre/bin/java
          4    /usr/bin/gij-4.1
          5    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 5


Thanks for your help.

---

