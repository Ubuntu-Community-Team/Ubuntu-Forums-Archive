---
title: "Installing Kernel 4.9 on Ubuntu 16.04 Ubuntu"
date: 2016-12-13
forum: Desktop Environments
---

### Post by deepakdeshp on 2016-12-13
Hello,

For AMD a8 64 bit processor  is the following code correct to install Kernel 4.9? If not, please direct for installing Kernel 4.9.

Thank you for your help
```
cd /tmp/

wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.9/linux-headers-4.9.0-040900_4.9.0-040900.201612111631_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.9/linux-headers-4.9.0-040900_4.9.0-040900.201612111631_all.deb)

wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.9/linux-headers-4.9.0-040900-generic_4.9.0-040900.201612111631_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.9/linux-headers-4.9.0-040900-generic_4.9.0-040900.201612111631_amd64.deb)

wget [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.9/linux-image-4.9.0-040900-generic_4.9.0-040900.201612111631_amd64.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.9/linux-image-4.9.0-040900-generic_4.9.0-040900.201612111631_amd64.deb)

sudo dpkg -i *.deb

```

---

### Post by #&amp;thj^% on 2016-12-13
That's how I did it.;)
```
System:    Host: me-System-Product-Name Kernel: 4.9.0-040900-lowlatency x86_64 (64 bit)
           Desktop: Unity 7.4.0  Distro: Ubuntu 16.04 xenial

```
BTW you won't get the low-latency but the generic.
I chose the low-latency...to clear this up a bit.

---

### Post by deepakdeshp on 2016-12-13
> **1fallen said:**
> That's how I did it.;)
```
System:    Host: me-System-Product-Name Kernel: 4.9.0-040900-lowlatency x86_64 (64 bit)
           Desktop: Unity 7.4.0  Distro: Ubuntu 16.04 xenial

```
BTW you won't get the low-latency but the generic.
I chose the low-latency...to clear this up a bit.

Thank you . I wanted to know if the source was secure.  Building Kernel from a compromised source will be ill advised. :p. I am running on AMD A8 CPU hence the 64 bit version is fine.

---

### Post by #&amp;thj^% on 2016-12-13
Well that can be a double edged Question:
Here is the hosting server: Apache/2.4.18 (Ubuntu)** Server at kernel.ubuntu.com** Port 80
Unless someone has hacked it.. yes it is secure. 
All will say here is that I have had no bad mishaps security wise, and I have been here for 10 plus years...I know this is not what you wanted to hear, But like i said that can be a double edged Question.

---

### Post by deepakdeshp on 2016-12-13
No, I am not talking about the server getting hacked. Its the https and http protocol that set me thinking , just in case!

[COLOR=#333333][FONT=&amp]I am running AMD Radeon GPU. There are improvements in Kernel 4.9 for AMD Radeon . [/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]The official Ubuntu site is[/FONT][/COLOR]** [https://www.ubuntu.com]("https://www.ubuntu.com/")**[COLOR=#333333][FONT=&amp] and this site is [/FONT][/COLOR]**[http://www.ubuntu.com](http://www.ubuntu.com) .** And there is the PPA mentioned.

---

### Post by #&amp;thj^% on 2016-12-13
I'm not going to be able to answer your question in way that you will be happy with.
We all use it here: [https://ubuntuforums.org/showthread.php?t=2340133](https://ubuntuforums.org/showthread.php?t=2340133)
And sorry if that is not enough...I also have no advise on [COLOR=#333333][FONT=&amp]AMD Radeon GPU...As I am all Nvidia Here>
And your main question is "**For AMD a8 64 bit processor  is the following code correct to install  Kernel 4.9? If not, please direct for installing Kernel 4.9.**"
Which I feel I have at that point done a Fair Job.
[/FONT][/COLOR]

---

### Post by deepakdeshp on 2016-12-13
My question is about the security of ther downloaded sites  packages .If somebody says that downloading the deb packages from [COLOR=#333333] [/COLOR]**[http://www.ubuntu.com]("http://www.ubuntu.com/") ****is fine and **[COLOR=#333333] [/COLOR]**[https://www.ubuntu.com]("http://www.ubuntu.com/") , is not required that is fine.   Dpwnloading from http site is fine and https protocol is not required for the downloads. And yes the servers at http havent been hacked is my assumption**

---

### Post by deepakdeshp on 2016-12-16
No Kernel 4.9 did not work on my system , I didnt get the graphics desktop hence Iuninstalled kernel 4.9

---

