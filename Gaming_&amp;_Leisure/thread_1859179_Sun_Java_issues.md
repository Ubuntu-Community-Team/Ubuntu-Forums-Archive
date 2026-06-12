---
title: "Sun Java issues"
date: 2011-10-13
forum: Gaming &amp; Leisure
---

### Post by CarlP89 on 2011-10-13
I'm trying to download Sun Java to run Minecraft with because I heard OpenJDK wasn't recommended.

I'm using this installer [http://ubuntuforums.org/showthread.php?t=1726735&highlight=minecraft+installer](http://ubuntuforums.org/showthread.php?t=1726735&highlight=minecraft+installer), and when I select update/install Sun java I get this error message: 
Reading state information... Done

Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate



When I run sudo apt-get install sun-java6-jre in terminal, I get the same message. Any help?

I'm running 10.4.

---

### Post by donkyhotay on 2011-10-13
First of all I'd recommend using one of the regular package managers like apt-get, synaptic, or ubuntu software center rather then a script found online (even on a forum like this one). With that out of the way have you made certain openJDK is already uninstalled? If it is removed try:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install sun-java6-jre

```
to make certain the packages are all up to date before reinstalling sun java.

---

### Post by CarlP89 on 2011-10-13
> **donkyhotay said:**
> First of all I'd recommend using one of the regular package managers like apt-get, synaptic, or ubuntu software center rather then a script found online (even on a forum like this one). With that out of the way have you made certain openJDK is already uninstalled? If it is removed try:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install sun-java6-jre

```to make certain the packages are all up to date before reinstalling sun java.

Thanks for you help!

I checked synaptic, and I got a rather large list of things related to Sun Java, and I wasn't sure which of them to install. Would sun-javadb-common be the one I want? Also, I typed in Openjdk in synaptic and marked everything that was marked for complete removal, is that good enough?

---

### Post by Paulthefink on 2011-10-13
> **CarlP89 said:**
> Thanks for you help!

I checked synaptic, and I got a rather large list of things related to Sun Java, and I wasn't sure which of them to install. Would sun-javadb-common be the one I want? Also, I typed in Openjdk in synaptic and marked everything that was marked for complete removal, is that good enough?

I'm having this issue too. I'm new to ubuntu and linux, and I can't find sun java anywhere. The terminal thingy says it's obsolete or outdated and I have no clue where to find it in this synaptic thingy either...

---

### Post by ubupirate on 2011-10-13
> **Paulthefink said:**
> I'm having this issue too. I'm new to ubuntu and linux, and I can't find sun java anywhere. The terminal thingy says it's obsolete or outdated and I have no clue where to find it in this synaptic thingy either...

**NOTE: If you are running latest 11.10 Oneiric, please disregard this post and refer to the one below me @thatguruguy.**

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

You need to enable the Partner repository in your software sources list.

After you do:

```
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-jdk sun-java6-plugin sun-java6-fonts
```And if you have multiple Java installed:

```
sudo update-alternatives --config java
```And choose Sun Java as your default Java version to use.

---

### Post by thatguruguy on 2011-10-14
> **ubupirate said:**
> [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

You need to enable the Partner repository in your software sources list.

After you do:

```
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-jdk sun-java6-plugin sun-java6-fonts
```And if you have multiple Java installed:

```
sudo update-alternatives --config java
```And choose Sun Java as your default Java version to use.

The information given above is inaccurate for Ubuntu 11.10 and later.  Here is the current state of Java:

1. It should first be noted that there is no such thing as Sun Java anymore, because Sun was bought out by Oracle.

2. Oracle is [no longer distributing Java through third-party repositories]("http://robilad.livejournal.com/90792.html"). As mentioned in the link, the "official" Oracle jdk7 is based off the openjdk 7.

3. You now have two options.

[LIST]
[*]You can go to Oracle's website and download Java for free, but you'll have to install it manually, or
[*]You can install the openjdk7 java runtime environment from the Ubuntu repository by typing the following in a terminal:
[/LIST]
```
sudo apt-get install openjdk-7-jre
```

---

### Post by Paulthefink on 2011-10-14
> **ubupirate said:**
> **NOTE: If you are running latest 11.10 Oneiric, please disregard this post and refer to the one below me @thatguruguy.**

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

You need to enable the Partner repository in your software sources list.

After you do:

```
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-jdk sun-java6-plugin sun-java6-fonts
```And if you have multiple Java installed:

```
sudo update-alternatives --config java
```And choose Sun Java as your default Java version to use.

I'm actually using 10.4 still, thanks!

---

