---
title: "Update sun-java to secure version"
date: 2012-04-05
forum: Desktop Environments
---

### Post by ronaldv on 2012-04-05
Hi,

Ubuntu has stopped supporting sun-java because of licensing with open-jdk being the alternative. Now we can still install sun-java using the ppa:ferramroberto/java repository.

But the version from this repo is 1.6.0_26 which is insecure and will even be blocked by firefox in the very near future.

Manually installing the latest sun version is quite a hassle and must be re-done on every new security release. :-(

Are there any options to use update-manager/apt-get to keep the sun-java up-to-date? What is the general opinion on this?

[I feel that switching to open-jdk is tricky; I am afraid for incompatibilities because most java-code is written for sun-java.]

---

### Post by zombifier25 on 2012-04-05
There's no known updated PPA for Oracle Java, but you can always use this: [http://www.omgubuntu.co.uk/2012/01/sun-still-shines-for-java-users-on-ubuntu/](http://www.omgubuntu.co.uk/2012/01/sun-still-shines-for-java-users-on-ubuntu/)
It's a script that will automatically download the latest Oracle Java and install it. Credits to its creator.

---

### Post by ronaldv on 2012-04-06
Spot on:

$ java -version
java version "1.6.0_31"
Java(TM) SE Runtime Environment (build 1.6.0_31-b04)
Java HotSpot(TM) Server VM (build 20.6-b01, mixed mode)

---

