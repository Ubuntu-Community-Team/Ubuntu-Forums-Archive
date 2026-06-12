---
title: "Minecraft not working..."
date: 2013-04-04
forum: Gaming &amp; Leisure
---

### Post by 700 on 2013-04-04
Hi! 
Java is not working on my Ubuntu 11.10 64bit.
Why it's not working and how to fix it, plz? I've already tried everything I found about it.

Symptoms:
- Firefox: "Something is wrong. Java is not working." 
- [http://pasteall.org/pic/show.php?id=48554](http://pasteall.org/pic/show.php?id=48554)

Kind regards

---

### Post by peredur on 2013-04-04
Seems to me that your problem is with running Java applets in Firefox.  Is that right?  The Java VM outside of the browser seems just fine, I'd imagine, or it wouldn't reply to java - version.

Check your plugins in Firefox, if this is the case.  I have the IcedTea-Web 1.2 plugin installed.

If you're not trying to run an applet, some more detail about exactly what you're trying to do would be helpful.

---

### Post by QIII on 2013-04-04
Hello!  Sorry to hear you are having problems.

Could you please post the output of ```
java -version
```

---

### Post by 700 on 2013-04-04
peredur, QIII:
Some details you could see under this url: [http://pasteall.org/pic/show.php?id=48554](http://pasteall.org/pic/show.php?id=48554)
Minecraft is using Java and it's not working, as you see above.
Version of java, below:
```
~$ java -version
java version "1.7.0_17"
Java(TM) SE Runtime Environment (build 1.7.0_17-b02)
Java HotSpot(TM) 64-Bit Server VM (build 23.7-b01, mixed mode)
```
Thank you about concerns :)

---

### Post by peredur on 2013-04-04
If the problem is in Firefox, it's probably not the java vm on your box that is causing the problem.  It's more likely the java plugin in the browser which, as I said, is the IcedTea plugin in my browser.  But to be sure of the problem you're having I really think we need more details of what you're trying to do.  For example, are you getting the error message when you try to access a web site?  If so, what site?  Or are you trying to do something else?

Again, assuming the problem is in your browser, have you checked the browser plugin like I suggested above?  Is the java plugin installed?  Is it activated?

---

### Post by QIII on 2013-04-04
If you launch Minecraft from the terminal, are you getting a report of any errors?

---

### Post by 700 on 2013-04-04
Collection of symptoms:
- Java is installed;
- Plugin has been set (through the terminal), but it is not visible after "about : plugins" command on any browser (Chrome, Chromium, Firefox...);
- Minecraft is using Java, but it's not working as well (I'm not getting any errors - I used to get errors before, when minecraft was working);
- The message "Something is wrong. Java is not working." appears (obviously) on this website: [http://java.com/en/download/testjava.jsp](http://java.com/en/download/testjava.jsp) (Firefox is searching for suggested plugs, but it's not finding anything).

---

### Post by QIII on 2013-04-04
Would you try re-installing per the instructions at:

[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

---

### Post by 700 on 2013-04-04
Hmm... Java is working on browsers, but it is not working on Minecraft (no errors appeared).

---

### Post by QIII on 2013-04-04
OK.  I'm going to modify the title of your thread and move it over to Gaming & Leisure, since this might be better addressed by folks familiar with Minecraft.

*Thread moved to** Gaming & Leisure.***

---

### Post by Horbo on 2013-04-06
You are using Java 7, which minecraft doesn't like.  Install Java 6 and use that instead, it will work fine.


```
sudo add-apt-repository ppa:webupd8team/java[COLOR=#333333][FONT=Ubuntu] [/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR]sudo apt-get update && sudo apt-get install oracle-java6-installer
```

---

### Post by ppjdee on 2013-04-07
Minecraft working well for me.:)

```
java version "1.7.0_17"
OpenJDK Runtime Environment (IcedTea7 2.3.8) (7u17-2.3.8-1ubuntu1)
OpenJDK 64-Bit Server VM (build 23.7-b01, mixed mode)
```

---

### Post by Horbo on 2013-04-10
If you're replying to me ppjdee, I should have pointed out I was talking only about Oracle Java. ;-)  I have no experience with Openjava...

---

