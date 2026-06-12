---
title: "APT URL or Screenshot?"
date: 2010-06-30
forum: Forum Feedback &amp; Help
---

### Post by uRock on 2010-06-30
I couldn't help but notice the thread in the RC about a thread being closed because the OP just posted an apt-url with no explanation. Why would someone force readers to attempt and install with an apt-url? Wouldn't it be easier to take a few screenshots and post them. 

With social engineering being one of the only ways to attack a Linux system I feel that apt-urls are a bad idea, especially when there is no explanation of what it is going to do.

Thanx for reading,
uRock

---

### Post by cariboo on 2010-07-01
Personally I like apt-url, I explain what the link does whenever I use one.

---

### Post by jpeddicord on 2010-07-01
There is no security issue with using an apt:// protocol url as a link. apturl *always* asks the user if they'd like to install the named package, so there's no drive-by installs. Second, apturl is only capable of installing packages already available in the user's repositories, so if there's a security problem with something in the archives you'd want to take it up with the Ubuntu developers. apturl also cannot add extra repositories.

It's just a shortcut for installing packages on-the-fly.

---

