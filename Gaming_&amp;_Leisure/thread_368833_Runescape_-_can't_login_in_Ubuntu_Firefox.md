---
title: "Runescape - can't login in Ubuntu Firefox"
date: 2007-02-23
forum: Gaming &amp; Leisure
---

### Post by geezerone on 2007-02-23
Hi

Anyone having problems using Firefox to login to runescape? The username and password boxes are there but typing shows no text on screen. Strange indeed.

---

### Post by haricharan on 2007-02-23
it shows for me what i type.....unfortunately i forgot my username password and i m not able to login....

---

### Post by purplearcanist on 2007-02-23
Works perfectly for me.:) 

I personally think it is a waste of time, but since it is a Java game, try updating Java and downloading the latest fonts.

---

### Post by geezerone on 2007-02-23
I had Java JRE 1.5.06 installed already but installed Sun Java JDK 1.5 via automatix and now working. 

Out of interest how do you update java to latest?

Thanks.

---

### Post by tommyvyo on 2007-02-24
This is a bug in Java 1.5, if you click anywhere outside the applet it loses focus from the keyboard, and you are unable to type. I had the same problem and downgraded to 1.4 and it works fine now.

---

### Post by geezerone on 2007-02-28
Upgraded to jre 6 (via Synaptic) and now ok.

---

### Post by Guyon on 2009-08-21
I hate to bring back an ancient thread but I'm having this problem and can't seem to nail the problem. I've re-installed sun-java6-jre and rebooted but it still won't work.. any progress since early 2007?

---

### Post by geezerone on 2009-08-21
Have you checked which one is active? See [THIS]("https://help.ubuntu.com/community/Java") thread on Java.

To use sun java you would type:

```
sudo update-java-alternatives -s java-6-sun
```

---

