---
title: "How to install Java???"
date: 2005-10-17
forum: Desktop Environments
---

### Post by Fern_azul10 on 2005-10-17
im having trouble installing java I have tried the old method from the ubuntu guide but that doesnt work and I have seen several other guides on how to install it but to me who still new to linux is still to complicated is their anyone who can show me a easy step by step guide on how to install java? Please!!!!

---

### Post by unexpected on 2005-10-17
I installed Java 1.5 using the steps in this thread:

[http://www.ubuntuforums.org/showthread.php?t=70428&highlight=Java+1.5](http://www.ubuntuforums.org/showthread.php?t=70428&highlight=Java+1.5)

It was really painless, just follow the steps exactly, copy and paste the commands if you want to.

---

### Post by br00tal on 2005-10-18
This works for some (not for me), but check out the Ubuntu Wiki.  It's got info on how to install the free java software that comes with Ubuntu.

---

### Post by Segovia on 2005-10-18
[QUOTE=br00tal]This works for some (not for me), but check out the Ubuntu Wiki.  It's got info on how to install the free java software that comes with Ubuntu.[/QUOTE]
Are you referring to the Blackdown packages?  I'm wondering, does that work with Azureus?

---

### Post by yage on 2005-10-18
Azureus did'nt work with blackdown for me so i used the wiki guide and made a deb package of the 1.5 binaries.

---

### Post by FLeiXiuS on 2005-10-18
If it didn't work it's more then likely that you still have sun-j2re1.5 installed.

sudo apt-get install java-common
sudo dpkg -r sun-j2re1.5
sudo apt-get install j2re1.4

---

### Post by Segovia on 2005-10-18
I did the Sun Java install, thanks for the info on Blackdown, FLeiXiuS and yage.

So then I do an apt-get install azureus and to my surprise it's not on the breezy repos?  I could have sworn it was in universe or multiverse on Hoary?  Or was it Backports (obviously not enabled yet for Breezy)?  Regardless, I'm a little dissapointed not to find it there.

---

### Post by paddyg on 2005-10-18
That's in case Fern_azul10 hasn't sorted out the issue.

That's what I did and i'll always do:

I Just got jdk-1_5_0_05-linux-i586.bin from java.sun.com.
As root I made a /usr/java dir, saved the file there and unpacked it.
Then manually I made all the symlink for firefox (on my machine /usr/java/jdk1.5.0_04/jre/plugin/i386/ns7) and pasted it to firefox plugin dir (/usr/lib/mozilla-firefox/plugins)

Never used apt-get with Java.

---

