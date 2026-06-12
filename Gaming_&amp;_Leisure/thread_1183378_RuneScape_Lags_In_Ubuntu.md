---
title: "RuneScape Lags In Ubuntu"
date: 2009-06-10
forum: Gaming &amp; Leisure
---

### Post by BlazeFire247 on 2009-06-10
Whenever I go play RuneScape, it lags my computer. It was never like that on Windows. It lags whenever I go to the login screen, I can't even play it! How can I fix this?

Thanks,
BlazeFire

---

### Post by jyaan on 2009-06-10
Which Java are you using? I use sun-java6-plugin and the game runs great for me (in high-res mode). Maybe you should switch your Java version? You should be able to find out which Java you're running by doing this command in a teminal: ```
sudo update-java-alternatives -l
```
and then you can set it to one of the listed JVMs with
```
#so in my case it would be
sudo update-java-alternatives -s java-6-sun
```
Make sure you have sun-java6-plugin installed anyways.

---

### Post by BlazeFire247 on 2009-06-10
It says

```
java-6-openjdk 1061 /usr/lib/jvm/java-6-openjdk
java-6-sun 63 /usr/lib/jvm/java-6-sun
```

---

### Post by jyaan on 2009-06-10
Yea, you're probably running openjdk. Try switching to sun-java6 and see if it helps. Just use the command I listed before: ```
sudo update-java-alternatives -s java-6-sun
```

---

### Post by BlazeFire247 on 2009-06-10
Thanks! RuneScape runs perfectly fine now. :D

---

