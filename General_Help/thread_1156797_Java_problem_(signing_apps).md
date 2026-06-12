---
title: "Java problem (signing apps)"
date: 2009-05-12
forum: General Help
---

### Post by hackapelite on 2009-05-12
Well, I just tried checking my runescape account (I really don't play the game any more though), but it redirected me to a page where it said that it was unable to start it signed. Now, it never came up with the popup that asks whether I'd like to run the app or not, and if I want to trust the source (you know the one). What's wrong? I haven't been able to try any other java apps just yet, but I think I may have a problem...

Running 9.04

---

### Post by kpkeerthi on 2009-05-12
Click on this link to verify is your java Plugin if working

[http://www.java.com/en/download/installed.jsp?detect=jre&try=1]("http://www.java.com/en/download/installed.jsp?detect=jre&try=1")

---

### Post by hackapelite on 2009-05-12
It came up woth "Oops! You don't have the recommended Java installed". I went to downloads, but all they have os 4 different downloads - a BIN and an RPM, both for 32 and 64 bit. I downloaded the BINs (it said something like "please use the 32-bit for Java applet and Java Web Start"). Now what do I do with those BINs, or should I be doing anything with them at all?

---

### Post by kpkeerthi on 2009-05-12
What ubuntu release are you using?

[http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu-904-jaunty.html]("http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu-904-jaunty.html")

---

### Post by hackapelite on 2009-05-13
^> Well, I just tried checking my runescape account (I really don't play the game any more though), but it redirected me to a page where it said that it was unable to start it signed. Now, it never came up with the popup that asks whether I'd like to run the app or not, and if I want to trust the source (you know the one). What's wrong? I haven't been able to try any other java apps just yet, but I think I may have a problem...

**_*Running 9.04*_**;)

Thanks for the link, will give a shot...

---

### Post by hackapelite on 2009-05-13
Nope, didn't work. I typed in java -version, but the version number remains the same (1.6.0_0 instead of 1.6.0_13 which it should be). Also, it says OpenJDK, that's not the "official" sun-maintained thing is it?

---

### Post by hackapelite on 2009-06-13
*BUMP*

This is beginning to tick me off... doesn't work on my desktop either (running 9.04 as well). Tried the link in post #4, and while the installation goes through alright, the computer (well, Firefox at least) is still resorting to OpenJDK, which doesn't work! I tried disabling the IcedTea plugin in Addons, but then it disables libnpjp2 (presumably the "right" plugin) as well. "java -version" still comes up with the following:
> java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.4.1) (6b14-1.4.1-0ubuntu7)
OpenJDK 64-Bit Server VM (build 14.0-b08, mixed mode)

Help, anyone?

---

