---
title: "IcedTea Java doesn't work in google chrome"
date: 2010-08-29
forum: Desktop Environments
---

### Post by Firidan on 2010-08-29
Every time I visit any webpage that has java applets an error message pops up saying that IcedTea plug-in has crashed. Since java  work fine in firefox and Eclipse IDE I think it's a some kind of bug in chrome or IcedTea.

Thanks in advance!

---

### Post by gordintoronto on 2010-08-29
I suspect my approach is unpopular: when I want Java, I want the real thing.

If you Google cool shisen the first result is a Java game. Can you play it with Icedtea?

---

### Post by Firidan on 2010-08-30
Actually it does work :confused: . The game that doesn't work is need for madness 2 [http://www.radicalplay.com/madcars/](http://www.radicalplay.com/madcars/)
Runescape doesn't work either. How do I remove IcedTea and Open JDK and replace with Sun's JRE?

---

### Post by howefield on 2010-08-30
As far as I can see, Sun Java should peacefully co-exist with OpenJDK, so enabling the partner repository and installing sun-java6-jre sun-java6-plugin and sun-java6-fonts and then running in terminal

```
sudo update-alternatives --config java
```

should do the trick.

---

### Post by Firidan on 2010-08-31
Thanks! It worked.

---

