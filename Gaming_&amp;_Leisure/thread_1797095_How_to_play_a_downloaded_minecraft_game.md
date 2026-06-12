---
title: "How to play a downloaded minecraft game?"
date: 2011-07-04
forum: Gaming &amp; Leisure
---

### Post by phantom 2543 on 2011-07-04
I've installed minecraft on a windows computer, and now I have put it USB tumb drive but it wont execute on xubuntu. All help appreciated.

---

### Post by cre8ive65 on 2011-07-04
Ok, some things to keep in mind
As of 1.3 (dont qoute me on that) Minecraft no longer works with OpenJDK, you need Sun Java JRE

Go into System>Administration>Software Sources and make sure the "Multiverse" is enabled, then go into terminal and type
```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```
Once that's installed, you need to download minecraft from this link
[http://www.minecraft.net/download/minecraft.jar?v=1309833226429]("http://www.minecraft.net/download/minecraft.jar?v=1309833226429")
Then, right click the jar you just downloaded, go to "properties", go to the permissions tab and make sure "Allow executing file as program" box is check, next go to the "Open with" tab and select something along the lines of "Java runtime" and click close Double click the jar and you're good for business :)

Lemme know if you need any more help or if you are interested in playing on my server, ill whitelist you and give you my ip

---

### Post by phantom 2543 on 2011-07-05
Thanks.

---

