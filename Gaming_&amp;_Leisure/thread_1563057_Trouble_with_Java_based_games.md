---
title: "Trouble with Java based games"
date: 2010-08-28
forum: Gaming &amp; Leisure
---

### Post by Burky on 2010-08-28
I am using Ubuntu Lucid Lynx 32bit, Firefox 3.6.8, and Java 6 standard Edition Update 20 (build 1.6.0_20-b02). When ever I go to a java based video game such as Runegasm, after about 5 seconds the screen goes white. Any idea on how to fix this?

---

### Post by akoskm on 2010-08-28
> **Burky said:**
> I am using Ubuntu Lucid Lynx 32bit, Firefox 3.6.8, and Java 6 standard Edition Update 20 (build 1.6.0_20-b02). When ever I go to a java based video game such as Runegasm, after about 5 seconds the screen goes white. Any idea on how to fix this?

Do you have installed the java browser plugin? If not, then
```

sudo aptitude install sun-java6-plugin

```.
Could you post the output of
```

java -version

```?

---

### Post by Burky on 2010-08-28
```
java version "1.6.0_18"
OpenJDK Runtime Environment (IcedTea6 1.8.1) (6b18-1.8.1-0ubuntu1)
OpenJDK Server VM (build 16.0-b13, mixed mode)

```

---

### Post by akoskm on 2010-08-28
> **Burky said:**
> ```
java version "1.6.0_18"
OpenJDK Runtime Environment (IcedTea6 1.8.1) (6b18-1.8.1-0ubuntu1)
OpenJDK Server VM (build 16.0-b13, mixed mode)

```

I suggest you to replace the default OpenJDK installation with Sun JRE.
First remove the OpenJDK:
```

sudo aptitude remove openjdk-6-jre

```,
then install the SUN JRE and the browser plugin:
```

sudo aptitude install sun-java6-jre sun-java6-plugin

```.

---

### Post by Dayofswords on 2010-08-28
> **Burky said:**
> When ever I go to a java based video game such as Runegasm, after about 5 seconds the screen goes white. 

thats what you get for using a illegal private server...

---

### Post by lovinglinux on 2010-08-28
Ooops

---

