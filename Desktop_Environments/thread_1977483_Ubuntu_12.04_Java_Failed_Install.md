---
title: "Ubuntu 12.04 Java Failed Install"
date: 2012-05-10
forum: Desktop Environments
---

### Post by rigel4 on 2012-05-10
Hi I tried to install Java for Ubuntu 12.04 LTS and the install failed!
I am getting loads of random app crashes and spongy slow response of the system
in general.

I don't know how to remove what's been done or how to actually
get Java on the system.

Everything was good until this. I have copied the terminal
output for you to look at and maybe offer me a way out of this.

Reinstalling is not a good option right now, as i have a ton of data.

Thank you 


> 

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up oracle-java7-installer (7u3-0~eugenesan~precise4) ...
Downloading...
--2012-05-10 11:37:55--  [http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz](http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz)
Resolving download.oracle.com (download.oracle.com)... 92.123.154.83, 92.123.154.75
Connecting to download.oracle.com (download.oracle.com)|92.123.154.83|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz) [following]
--2012-05-10 11:37:55--  [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz)
Resolving edelivery.oracle.com (edelivery.oracle.com)... 2.18.210.174
Connecting to edelivery.oracle.com (edelivery.oracle.com)|2.18.210.174|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html) [following]
--2012-05-10 11:37:55--  [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html)
Connecting to download.oracle.com (download.oracle.com)|92.123.154.83|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5307 (5.2K) [text/html]
Saving to: `./jdk-7u3-linux-x64.tar.gz'

     0K .....                                                 100% 5.10M=0.001s

2012-05-10 11:37:55 (5.10 MB/s) - `./jdk-7u3-linux-x64.tar.gz' saved [5307/5307]

Download done.
sha256sum mismatch jdk-7u3-linux-x64.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
alex@U-Box:~$ sudo apt-get install  oracle-java7-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
oracle-java7-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up oracle-java7-installer (7u3-0~eugenesan~precise4) ...
Downloading...
--2012-05-10 11:38:47--  [http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz](http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz)
Resolving download.oracle.com (download.oracle.com)... 92.123.154.83, 92.123.154.75
Connecting to download.oracle.com (download.oracle.com)|92.123.154.83|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz) [following]
--2012-05-10 11:38:52--  [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz)
Resolving edelivery.oracle.com (edelivery.oracle.com)... 2.18.210.174
Connecting to edelivery.oracle.com (edelivery.oracle.com)|2.18.210.174|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html) [following]
--2012-05-10 11:38:53--  [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html)
Connecting to download.oracle.com (download.oracle.com)|92.123.154.83|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5307 (5.2K) [text/html]
Saving to: `./jdk-7u3-linux-x64.tar.gz'

     0K .....                                                 100% 3.49M=0.001s

2012-05-10 11:38:53 (3.49 MB/s) - `./jdk-7u3-linux-x64.tar.gz' saved [5307/5307]

Download done.
sha256sum mismatch jdk-7u3-linux-x64.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
alex@U-Box:~$ 


---

### Post by rigel4 on 2012-05-10
HI I have solved it myself from a post elsewhere:



```
sudo rm /var/lib/dpkg/info/oracle-java7-installer* sudo apt-get purge oracle-java7-installer* sudo rm /etc/apt/sources.list.d/*java* sudo apt-get update sudo add-apt-repository ppa:webupd8team/java sudo apt-get update sudo apt-get install oracle-java7-installer
```

---

### Post by Helopoh on 2012-05-10
I could kiss you.. 2 days of looking and you solved it for me in 3 minutes. Thanks a Bunch!
:popcorn:

---

### Post by bsprakash on 2012-05-15
**Rigel / Helopoh,**

Can you tell me the clear commands? if possible step by step
I am facing same problem

The commands you given i tried.
Instead of symbols what i have to use.?

Please forgive me.. I am not good in Linux.

Expecting your best response ASAP.

---

### Post by ibussieres on 2012-05-15
Thanks guys, worked perfectly for me.

Try this bsprakash, if you're unsure, one command at a time.

```
sudo rm /var/lib/dpkg/info/oracle-java7-installer*
sudo apt-get purge oracle-java7-installer*
sudo rm /etc/apt/sources.list.d/*java*
sudo apt-get update
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```

Or all in one :

```
sudo rm /var/lib/dpkg/info/oracle-java7-installer*; sudo apt-get purge oracle-java7-installer*; sudo rm /etc/apt/sources.list.d/*java*; sudo apt-get update; sudo add-apt-repository ppa:webupd8team/java; sudo apt-get update; sudo apt-get install oracle-java7-installer;
```

---

### Post by Sinful Skiz on 2012-05-16
Words cannot describe how much I appreciate this fix. I was going absolutely bonkers. I'm a newbie to Ubuntu but I love the vast helpful community it creates. Thanks again! :grin:

---

### Post by osamakhn on 2012-05-20
Thank you so much for posting the fix!
This has been bugging me for almost a month now.

I have put the commands into a small script and a descriptive blog post here:

[http://www.osamakhan.com/blog/installing-oracle-java-on-ubuntu-1204-with-error-fix](http://www.osamakhan.com/blog/installing-oracle-java-on-ubuntu-1204-with-error-fix)

Hope this reaches whoever is having the same problem :)

---

### Post by rigel4 on 2012-05-24
I'm very pleased my thread helped the community out, but it was not my fix, i found this
in some obscure blog.

Thanks though to whoever i got it from.

:KS

---

### Post by ytkuser12 on 2012-05-26
thank you all new to ubuntu had issues thanks for this fix :)

---

### Post by QIII on 2012-05-27
Canonical didn't decide not to include Oracle Java.  Oracle decided to remove all licensing for Oracle Java to be maintained in anyone's repos.

---

### Post by QIII on 2012-05-27
Canonical didn't decide not to include Oracle Java.  Oracle decided to remove all licensing for Oracle Java to be maintained in anyone's repos.

---

### Post by ottosykora on 2012-05-27
I have one program which will definitely not run with the open java included in ubuntu otherwise, but other things seem to work fine.

Are there any special reasons why to install the oracle java instead the open java?

---

### Post by QIII on 2012-05-27
I give a brief explanation in the post in the link in my signature.

---

### Post by serjinsky on 2012-07-02
I used this fix in the past, and it seemed to work perfectly. But today, the error randomly started occurring again. When I attempted to use the same fix, it came up with a new error:

> Errors were encountered while processing:
 myspell-st
E: Sub-process /usr/bin/dpkg returned an error code (1)

If anyone can help with that, I'd be very grateful :)

---

### Post by vanhai on 2012-08-05
Following up your CLI, It is workable on my system. Thanks guys ^_~
> **ibussieres said:**
> Thanks guys, worked perfectly for me.

Try this bsprakash, if you're unsure, one command at a time.

```
sudo rm /var/lib/dpkg/info/oracle-java7-installer*
sudo apt-get purge oracle-java7-installer*
sudo rm /etc/apt/sources.list.d/*java*
sudo apt-get update
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```Or all in one :

```
sudo rm /var/lib/dpkg/info/oracle-java7-installer*; sudo apt-get purge oracle-java7-installer*; sudo rm /etc/apt/sources.list.d/*java*; sudo apt-get update; sudo add-apt-repository ppa:webupd8team/java; sudo apt-get update; sudo apt-get install oracle-java7-installer;
```

---

### Post by masonmd1 on 2012-08-22
> **rigel4 said:**
> HI I have solved it myself from a post elsewhere:



```
sudo rm /var/lib/dpkg/info/oracle-java7-installer* sudo apt-get purge oracle-java7-installer* sudo rm /etc/apt/sources.list.d/*java* sudo apt-get update sudo add-apt-repository ppa:webupd8team/java sudo apt-get update sudo apt-get install oracle-java7-installer
```

Oh, man, thank you so much. Spent hours looking at other forums and trying different ideas to install Java. This worked! Thanks.

---

### Post by gunbuck on 2012-08-30
I could kiss you thank you all working now great work cheers xD

---

### Post by Joe I on 2012-09-06
Thank You! After more than a week of digging your method worked! May you bump into something you really need!

---

### Post by Tyler Lusk on 2012-09-13
> **ibussieres said:**
> Thanks guys, worked perfectly for me.

Try this bsprakash, if you're unsure, one command at a time.

```
sudo rm /var/lib/dpkg/info/oracle-java7-installer*
sudo apt-get purge oracle-java7-installer*
sudo rm /etc/apt/sources.list.d/*java*
sudo apt-get update
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```Or all in one :

```
sudo rm /var/lib/dpkg/info/oracle-java7-installer*; sudo apt-get purge oracle-java7-installer*; sudo rm /etc/apt/sources.list.d/*java*; sudo apt-get update; sudo add-apt-repository ppa:webupd8team/java; sudo apt-get update; sudo apt-get install oracle-java7-installer;
```


Very Nice...Than you!

---

