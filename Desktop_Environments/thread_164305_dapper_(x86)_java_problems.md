---
title: "dapper (x86) java problems"
date: 2006-04-22
forum: Desktop Environments
---

### Post by funkyade on 2006-04-22
hi folks,

I've mysteriously started having a weird java problem on a new install.

when I execute the following, with app.jar being ANY .jar application, i.e. frostwire, phex etc... -

```
$>java app.jar
```

I get -

```
Exception in thread "main" java.lang.NoClassDefFoundError: app.jar 
```

I got this using SUN java, but after installing and trying every java variant possible, I get it in ALL. I have installed the library that should provide the java.lang classes, but it hasn't made any difference. (have used update-alternatives btw)

Completely bemused. Any help appreciated! thanks

fa

---

### Post by eitan on 2006-04-24
try

```
java -jar app.jar
```

---

### Post by funkyade on 2006-10-24
> **eitan said:**
> try

```
java -jar app.jar
```

doh! ](*,) 

thx

---

