---
title: "Java Issue when playing Yahoo games"
date: 2011-06-27
forum: Gaming &amp; Leisure
---

### Post by d0nut on 2011-06-27
Hello.  I recently installed Ubuntu.  I am trying to play yahoo pool in a java environment.  It loads and I can play, but it wont let me type in the chat area.  Ive tried firefox and chrome. Any ideas why?  I havent tried other yahoo games besides Pool but I'm sure its the same story... Thanks for any suggestions!

---

### Post by Virus666 on 2011-06-28
Are you sure that you are using the **Sun**'s version of Java? In order to check it;

```
sudo update-alternatives --config java
```Then select "java-6-sun." Personally, I do not use OpenJDK; if it is exists in your system, you may delete in via Synaptic unless you do not need it...

[https://help.ubuntu.com/community/Java#Choosing%20the%20default%20Java%20to%20use]("https://help.ubuntu.com/community/Java#Choosing%20the%20default%20Java%20to%20use")

---

