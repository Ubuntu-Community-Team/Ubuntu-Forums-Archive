---
title: "Installing JRE on Ubuntu 10.04"
date: 2012-03-30
forum: Desktop Environments
---

### Post by talha099 on 2012-03-30
I am very new to Ubuntu. I am trying to install JRE on Ubuntu 10.04.

I add the partner repository using the following command:

sudo add-apt-repository “deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner”

However when I run:

sudo apt-get update

I get the following error:

E: Malformed line 54 in source list /etc/apt/sources.list (dist parse)

Can someone please tell me what's going wrong? It'll be greatly appreciated. Thanks a lot!

---

### Post by Paddy Landau on 2012-03-30
Remove that repository and instead add:
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

You can do this in the GUI, if you prefer: System > Administration > Software Sources.

---

### Post by cyiucsy on 2012-03-30
I am not an expert on this but perhaps you can give us more details by posting your sources.list

Press Alt+F2 (Run Application), type:
```
gedit /etc/apt/sources.list
```
and press ENTER, then copy the contest of the sources.list file here. Hopefully then someone will be able to spot out the cause of the problem.

---

### Post by QIII on 2012-03-30
That will, however, leave you with an old Java update with some security issues.  Java 6 is now up to Update 31.

I'm on my cell phone on a train, so I can't give you the link.  However, if you google the following terms you will find an excellent, well-explained tutorial for installing Update 31:

```
easy linux tips java
```

Oracle has withdrawn all Sun's previous license agreements and distributions are no longer allowed to maintain the Sun packages as part of their freely downloadable software.

---

### Post by talha099 on 2012-03-30
It worked.. thanks a lot!


> **QIII said:**
> That will, however, leave you with an old Java update with some security issues.  Java 6 is now up to Update 31.

I'm on my cell phone on a train, so I can't give you the link.  However, if you google the following terms you will find an excellent, well-explained tutorial for installing Update 31:

```
easy linux tips java
```Oracle has withdrawn all Sun's previous license agreements and distributions are no longer allowed to maintain the Sun packages as part of their freely downloadable software.

---

### Post by sammiev on 2012-03-30
I suggest you try [This]("http://sites.google.com/site/easylinuxtipsproject/java"). You need the latest version to help keep your computer protected.

---

### Post by Paddy Landau on 2012-03-31
> **talha099 said:**
> It worked.. thanks a lot!
Excellent. Please [mark this thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

