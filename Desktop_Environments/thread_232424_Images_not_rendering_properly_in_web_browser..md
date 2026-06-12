---
title: "Images not rendering properly in web browser."
date: 2006-08-08
forum: Desktop Environments
---

### Post by karamba_kid on 2006-08-08
Last night I removed sun java that I had installed manually and installed sun java from the repositories, now I'm having images (I think it's only gifs) not rendering properly in both firefox and konq.  I'm not sure if this is related to me switching my java around, but I'm guessing that it is.  Can anyone help me?  I'll attach a screenshot so you can see what I'm talking about (look at the logo for scopetech website).

---

### Post by Jagot on 2006-08-08
I wouldn't have thought it should be related to Java, but just to check, make sure you have your newly installed Java selected corectly and try again:

```
sudo update-alternatives --config java
```

---

### Post by karamba_kid on 2006-08-08
here is my setup for java > $ sudo update-alternatives --config java

There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
      2        /usr/bin/gij-wrapper-4.1
 +    3        /usr/lib/jvm/java-gcj/jre/bin/java
*     4        /usr/lib/jvm/java-1.5.0-sun/jre/bin/java


any other suggestions as to what it could possibly be?

---

### Post by karamba_kid on 2006-08-12
This problem seems to be caused by privoxy and/or tor whichever one would make more sense.

---

