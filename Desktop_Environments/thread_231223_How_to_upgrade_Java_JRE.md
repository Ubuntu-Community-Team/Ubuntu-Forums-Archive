---
title: "How to upgrade Java JRE"
date: 2006-08-07
forum: Desktop Environments
---

### Post by magnoliablossom on 2006-08-07
I just installed frostwire and it wouldn't run.  It is telling me I need to upgrade my Java JRE.  How do I do this?  This is the message I get:

> heaven@ubuntu:~$ which frostwire
/usr/bin/frostwire
heaven@ubuntu:~$ /usr/bin/frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
heaven@ubuntu:~$



This link, especially the 2nd post, will tell you how to fix it...just in case anyone else had this problem....[http://ubuntuforums.org/showthread.php?t=207477&highlight=frostwire]("http://ubuntuforums.org/showthread.php?t=207477&highlight=frostwire")

Select option 3

---

### Post by Jagot on 2006-08-07
Enable the multiverse repository as demonstrtaed on either of these links:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
[http://psychocats.net/ubuntu/sources.php](http://psychocats.net/ubuntu/sources.php)

Then:

```
sudo aptitude update && sudo aptitude install sun-java5-bin
```

---

### Post by magnoliablossom on 2006-08-07
> **Jagot said:**
> Enable the multiverse repository as demonstrtaed on either of these links:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
[http://psychocats.net/ubuntu/sources.php](http://psychocats.net/ubuntu/sources.php)

Then:

```
sudo aptitude update && sudo aptitude install sun-java5-bin
```



Thanks....Not to sound dumb or anything which I know I will anyway but....are there supposed to be two "&" there?  The reason I'm asking is because i'm going to copy and paste. lol

---

### Post by magnoliablossom on 2006-08-07
Another question....When adding these extra repositories some of them are telling me "failed"....I'm thinking that's bad thing but hoping that it's not....?

---

### Post by magnoliablossom on 2006-08-07
Synaptic is showing that as installed but I am still getting that message telling that I need to update it.  What am I doing wrong?

---

### Post by Jagot on 2006-08-07
Ok, run this command and try again:

```
sudo update-java-alternatives -s java-1.5.0-sun
```

---

