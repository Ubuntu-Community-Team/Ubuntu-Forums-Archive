---
title: "Frostwire problems, wont launch"
date: 2006-09-05
forum: Desktop Environments
---

### Post by WalmartSniperLX on 2006-09-05
I installed frostwire but it wont launch. Using the java --version command i know i have version 1.4.2 

Does anyone know what is wrong?

---

### Post by wjp.reg on 2006-09-05
This has been dealt with on the [Frostwire forum]("http://www.frostwire.com/forum/viewtopic.php?t=454")

good luck.

---

### Post by taurus on 2006-09-05
Frostwire won't launch is not going to help anybody!  You need to run it from a terminal to see what the error message it...

---

### Post by WalmartSniperLX on 2006-09-05
> **taurus said:**
> Frostwire won't launch is not going to help anybody!  You need to run it from a terminal to see what the error message it...

I understand that. Was just hoping that someone else had a problem similar so i kept it basic :p  

Im not in ubuntu, infact im not home right now but it said that it cannot find java in the following paths (then it showed those dirs). But this doesnt make sense since i have java already ](*,)

---

### Post by WalmartSniperLX on 2006-09-05
> **wjp.reg said:**
> This has been dealt with on the [Frostwire forum]("http://www.frostwire.com/forum/viewtopic.php?t=454")

good luck.
Thank you. Ill go there and check it out :D

---

### Post by taurus on 2006-09-05
What is the output of this command from a terminal then?

```
java -version
```

---

### Post by WalmartSniperLX on 2006-09-05
> **taurus said:**
> What is the output of this command from a terminal then?

```
java -version
```

patrick@patrick-desktop:~$ java --version
java version "1.4.2"
gij (GNU libgcj) version 4.1.0 (Ubuntu 4.1.0-1ubuntu8)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

---

### Post by cstudent on 2006-09-05
Have you tried everything on this page?

[https://help.ubuntu.com/community/FrostWire](https://help.ubuntu.com/community/FrostWire)

---

### Post by WalmartSniperLX on 2006-09-05
> **cstudent said:**
> Have you tried everything on this page?

[https://help.ubuntu.com/community/FrostWire](https://help.ubuntu.com/community/FrostWire)

o no i havnt! Thanks! Ill do that in a bit, right now im eating a burger.. yeah!:D

---

### Post by WalmartSniperLX on 2006-09-05
Ok did what it said on the very bottom. That was where i was stuck. But, it said to select the dir with 'sun' in the title. I dont have one. Im guessing i should just do a clean install of the newer java sun 1.5? I just downloaded the .deb package. How should I install it?

---

### Post by WalmartSniperLX on 2006-09-05
**OKOK got java working... BUT** When i reinstalled frostwire, it isnt making the launcher anymore....wtf :S ](*,)

---

### Post by llamakc on 2006-09-05
What's the output of

```

update-alternatives --list java

```

I had to do 

```

sudo update-alternatives --config java

```


and choose the correct version. You're not running Edgy, are you?

---

### Post by WalmartSniperLX on 2006-09-05
> **llamakc said:**
> What's the output of

```

update-alternatives --list java

```

I had to do 

```

sudo update-alternatives --config java

```


and choose the correct version. You're not running Edgy, are you?

I dont think so

[I] patrick@patrick-desktop:~$ update-alternatives --list java
/usr/bin/gij-wrapper-4.1
/usr/lib/jvm/java-gcj/jre/bin/java
/usr/lib/jvm/java-1.5.0-sun/jre/bin/java
patrick@patrick-desktop:~$
[/I]

---

### Post by llamakc on 2006-09-05
Mine points to:

```

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
 +    2        /usr/lib/jvm/java-gcj/jre/bin/java
*     3        /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

Press enter to keep the default
[*], or type selection number:

```

. . .the Sun version.


Frostwire started just fine for me (just now).

---

### Post by DougieFresh4U on 2006-09-06
I'm still quite new to this, but I had the same issue & quickly learned I needed both java 1.4 and then sun java 5.0 which I found in my add/remove programs & synaptic. Hope this might help ](*,)

---

